<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <p>
        <input v-model="alienTodo" type="text" v-on:keyup.enter="nowTodo" size="50">
        <input type="submit" @click="addTodo">
    <p/>
    <ul>
      <li v-for="(item,index) in items" :key="item.id">
        <input type="checkbox" id="checkbox" v-model="item.complete">
        <label for="checkbox">{{item.index}}</label>
        <del v-if="item.checkbox">{{index}}.{{item.message}}</del>
        <span v-else>{{index}}.{{item.message}}</span>

      </li>
    </ul>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    //HelloWorld
  },
  data(){
    return {
      alienTodo: "",
    items: [
      { id: 1, message: 'Foo',checkbox:false },
      { id: 2, message: 'Bar', checkbox:false}
    ]
  }
  },
  methods: {
    nowTodo({target}){
      console.log(target.value);
    },
    addTodo() {
      this.items.push({ id: Date.now(), message: this.alienTodo });
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
  margin-top: 60px;
}
</style>
