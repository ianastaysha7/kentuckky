<template>
  <div id="app" class="picture1">
    <div class="picture2"><img alt="Vue logo" src="./assets/logo.png">
      <!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
      <label>
        Введите текст:
        <input v-model="newtodo" type="text" v-on:keyup.enter="addTodo" ><input type="submit" @click="addTodo">
      </label>

      <ul>
        <li v-for="(item, index) in itemsa" :key="item.id">
          <i class="far fa-check-circle"></i>
          <input type="checkbox" v-model="item.complete" @change="itemChanged(index)"> <span :class="{'del': item.complete}">{{index}}: {{ item.message }}</span>
          <button @click="removeTodo(index)">удалить</button>
          <!--        {{index }}<span v-if="item.complete">Выполнен</span>-->
          <!--        <span v-else>не Выполнен</span>-->

          <!--          <s v-if="item.complete"> Выполнено</s>-->
          <!--          <span v-else> Не выполнено</span>-->
        </li>
      </ul>
      <button @click="checkAll">отметить все</button>
    </div>

  </div>
</template>

<script>
  // import HelloWorld from './components/HelloWorld.vue'
  var moment = require('moment');
  console.log(moment().format());
  export default {
    name: 'App',
    components: {
      // HelloWorld
    },
    data() {
      return {
        newtodo: "",
        name1: "1231",
        name2: "12312",
        checkedAll: false,
        itemsa: [
          { id:123, message: 'Foo', complete: true },
          { id:2, message: 'Foo', complete: false },
          { id:3, message: 'Bar', complete: false }
        ]
      }
    },
    methods: {
      nowTodo({target}) {
        console.log(target.value);
      },
      addTodo() {
        this.itemsa.push({id: Date.now(), message: this.newtodo, complete: false });
        this.newtodo = "";
      },
      removeTodo(index) {
        this.itemsa.splice(index, 1);
      },
      checkAll() {
        for (var i = 0; i < this.itemsa.length; i++) {
          this.itemsa[i].complete = !this.checkedAll;
        }
        this.checkedAll = !this.checkedAll;
      },
      itemChanged(index) {
        if(!this.itemsa[index].complete && this.checkedAll) this.checkedAll=!this.checkedAll;
        // !this.itemsa[index].complete&&this.checkedAll?this.checkedAll=!this.checkedAll:'';
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Baloo+Paaji+2:wght@500&display=swap');
  <body>
  @font-face {
    font-family: 'Baloo Paaji 2', cursive;
  }
  </body>
  .picture1 {
    background-color: darksalmon;
    height: 500px;
    width: 1000px;
    background-position: center;
  }
  .picture2 {
    background-color: blueviolet;
    height: 300px;
    width:500px;
    background-position: right center 50px;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .del {
    text-decoration: line-through;
  }
  .hover {color: red, cursor: pointer; }
  .hover: hover, p {
    color: green;
  }
</style>