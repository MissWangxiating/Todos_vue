<template>
  <div id="app">
    <h1>{{title}}</h1>
    <input v-model="newItem" v-on:keyup.enter="addNew" type="text" name="mybox">
    <ul>
      <li v-for="item in items" :key="item.id" v-bind:class="{finished:item.isFinished}" v-on:click=" togglefinish(item) ">
        {{item.label}}
      </li>
    </ul>
    <p>child tells me:{{childwords}}</p>
    <component-a msgfromfather="you are going to die" v-on:child-tell-me-something='listenToMyBoy'></component-a>
  </div>

</template>

<script>
import Store from "./store.js"
import componentA from "./components/componentA"
export default {
  data: function (argument) {
    // body...
    return {
      title: 'this is a todo list',
      items: Store.fetch(),
      newItem: '',
      childwords:''

    }
  },
  components:{componentA}, //引入组件
  watch: {
    items:{
      handler:function (items){
        Store.save(items)
      },
      deep: true
      }
    },

  methods: {
    togglefinish: function (item) {
      // console.log(item)
      item.isFinished = !item.isFinished
    },
    addNew: function () {
      this.items.push({
        label: this.newItem,
        isFinished: false
      })
      this.newItem = ''
    },
    listenToMyBoy: function(msg){
      console.log(msg);
      this.childwords = msg;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finished{
  text-decoration: underline;
}
</style>
