<template>
  <div id="todo">
    <h1>My Todos</h1>
    <div v-for="todo in todos" :key="todo.index">
      <input type="checkbox" v-model="todos.isDone" />
      {{todo.index}}:{{todo.content}}
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
  data () {
    return {
      todos: [],
      input: ''
    }
  },
  computed: {
    lefts () {
      return this.todos.filter(function (t) {
        return !t.isDone
      }).length
    }
  },
  created: function () {
    this.title = 'My Todos'
    var saved = [
      {
        index: 1,
        isDone: true,
        content: 'content1'
      },
      {
        index: 2,
        isDone: false,
        content: 'content2'
      },
      {
        index: 3,
        isDone: false,
        content: 'content3'
      },
      {
        index: 4,
        isDone: false,
        content: 'content4'
      }
    ]
    for (var i = 0; i < saved.length; i++) {
      this.todos.push(saved[i])
    }
  },
  methods: {
    addTodo: function () {
      if (this.input === '') return
      var indexNum = this.todos.length + 1
      this.todos.push({ index: indexNum, content: this.input, isDone: false })
      this.input = ''
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
