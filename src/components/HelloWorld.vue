<template>
  <div id="app">
    <h1>My Todos</h1>
    <div v-for="item in items" :key="item.index">
      <input type="checkbox" v-model="item.isDone" />
      {{$index}}:{{t.content}}
    </div>
    <input type="text" v-model="input" value="">
    <input type="button" v-on:click="addTodo" value="add todo" />
    <div>
        left {{lefts}} tasks.
    </div>
  </div>
</template>

<script>
export default {
  el: '#todo',
  data:function() {
    return {
      todos: [
        {index:0, content:'', isDone:false}
      ]
    }
  },
  computed: {
    lefts: function(){
      return this.todos.filter(function(t){ return !t.isDone }).length;
    }
  },
  created: function(){
    this.title = "My Todos";
    var saved = [
      {
        isDone:true,
        content:"content1"
      },
      {
        isDone:false,
        content:"content2"
      },
      {
        isDone:false,
        content:"content3"
      },
      {
        isDone:false,
        content:"content4"
      }
    ]
    for(var i = 0; i < saved.length; i++){
      this.todos.push(saved[i]);
    }

  },
  methods:{
    addTodo: function(){
      if ( this.input === '' ) return;
      this.todos.push({ index:this.todos.slice(-1)[0], content:this.input, isDone:false });
      this.input = ""
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
