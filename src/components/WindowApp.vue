<template>
  <div class="window">
    <div class="top">
      <ul class="top__list">
        <li class="top__list-item item-red"><a class="top__button"></a></li>
        <li class="top__list-item item-yellow"><a class="top__button"></a></li>
        <li class="top__list-item item-green"><a class="top__button"></a></li>
      </ul>
    </div>

    <div class="bottom">
      <div class="search">
        <label class="search__text" for="inputSearch">Filter prefix: </label>
        <input type="search" class="search__input" id="inputSearch" v-model="prefix" @input="searchName" />
      </div>

      <div class="table">
        <div class="table__list">
          <select class="table__select" v-model="selectName" size="6">
            <option v-for="name in filterNames" :key="name" :value="name">{{ name }}</option>
          </select>
        </div>

        <div class="table__inputs">
        <div class="table__name">
          <label for="inputName">Name: </label>
          <input type="text" id="inputName" v-model="firstName"/>
        </div>

        <div class="table__surname">
          <label for="inputSurname">Surname: </label>
          <input type="text" id="inputSurname" v-model="lastName" />
        </div>
      </div>
      </div>

      <div class="buttons">
        <button class="buttons__btn" @click="createName">Create</button>
        <button class="buttons__btn" @click="updateName" :disabled="!selectName">Update</button>
        <button class="buttons__btn" @click="deleteName" :disabled="!selectName">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      prefix: "",
      firstName: "",
      lastName: "",
      selectName: "",
      names: [],
    }
  },

  computed: {
    filterNames() {
      return this.names.filter(name => name.startsWith(this.prefix))
    }
  },

  methods: {
    searchName() {
      this.selectName = '';
    },
    createName() {
      const newName = `${this.firstName} ${this.lastName}`;
      this.names.push(newName);
    },
    updateName() {
      const newName = `${this.firstName} ${this.lastName}`;
      const index = this.names.indexOf(this.selectName);
      if (index !== -1) {
        this.names[index] = newName;
      }
    },
    deleteName() {
      const index = this.names.indexOf(this.selectName);
      if (index !== -1) {
        this.names.splice(index, 1);
        this.selectName = '';
    }
  }
}
}
</script>
