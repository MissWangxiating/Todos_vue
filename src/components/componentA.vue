<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{msgfromfather}}</h2>
    <button v-on:click="onclickme">open mouse!</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to componentA'
    }
  },
  props:['msgfromfather'],
  methods: {
    onclickme: function ( ) {
      // body...
      console.log(this.msgfromfather);
      this.$emit('child-tell-me-something',this.msg);
    } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
