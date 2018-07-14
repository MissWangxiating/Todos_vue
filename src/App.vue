<template>
  <div id="app">
    <h1>{{title}}</h1>
    <input v-model="newItem" v-on:keyup.enter="addNew" type="text" name="mybox">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="togglefinish(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function(argument) {
    // body...
    return{
      title:"this is a todo list",
      items:[
      {
        label:"coding",
        isFinished:false
      },
      {
        label:"walking",
        isFinished:true
      }
      ]
    }
  },
  methods:{
    togglefinish: function(item){
      //console.log(item)
      item.isFinished = !item.isFinished;
    },
    addNew:function(){
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem=" "
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
