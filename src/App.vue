<template>
  <div id="app">
    <button @click="postIDs(elems)">
      Отправить ID отмеченных элементов
    </button>
    <list
    v-bind:elems="elems"
    @change-elem="changeColor"
    />
  </div>
</template>

<script>
import list from "@/components/list"
import axios from 'axios';
export default {
  name: 'App',
  data() {
    return {
      elems: [
        {id: 1, name: "Первый", active: false},
        {id: 2, name: "Второй", active: false},
        {id: 3, name: "Третий", active: false},
        {id: 4, name: "Четвертый", active: false},
        {id: 5, name: "Пятый", active: false},
        {id: 6, name: "Шестой", active: false},
        {id: 7, name: "Седьмой", active: false},
        {id: 8, name: "Восьмой", active: false},
        {id: 9, name: "Девятый", active: false},
        {id: 10, name: "Десятый", active: false},
        {id: 11, name: "Одиннадцатый", active: false},
        {id: 12, name: "Двенадцатый", active: false},
        {id: 13, name: "Тринадцатый", active: false},
        {id: 14, name: "Четырнадцатый", active: false},
        {id: 15, name: "Пятнадцатый", active: false},
        {id: 16, name: "Шестнадцатый", active: false},
        {id: 17, name: "Семнадцатый", active: false},
        {id: 18, name: "Восемнадцатый", active: false},
        {id: 19, name: "Девятнадцатый", active: false},
        {id: 20, name: "Двадцатый", active: false},
      ]
    }
  },
  components: {
    list
  },
  methods: {
    changeColor(el) {
      el.active = !el.active
    },
    sortMass(els) {
      let mass = [];
      for (let i = 1; i < els.length; i++) {
        if (els[i].active)
          mass.push(els[i].id)
      }
      return mass
    },
    postIDs(data) {
      let mass = this.sortMass(data)
      axios.post(`http://THE_NAME_OF_YOUR_SERVER/api/records/`, mass)
          .then(console.log)
          .catch(console.error)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
button {
  width: 100%;
  padding: 1rem;
  margin-top: 1rem;
  margin-bottom: 1rem;
}

</style>
