<template>
  <div class="hello">
    <h1>{{title}}</h1>
    <input type="" name="" v-model = "newTodo" @keyup.enter = 'addNew'>
    <ul>
      <li v-for='(todo, index) in todos' :id="index" :class= "{'done':todo.done}" @click='toggleDone(todo)'>
        <label>{{index + 1}}.{{todo.value}}</label>
      </li>
    </ul>
  </div>
</template>

<script>
import Store from '../store'
console.log(Store)
export default {
  name: 'hello',
  data () {
    return {
      title: 'this is a vue-todolist',
      todos: Store.fetch(),
      newTodo: ''
    }
  },
  methods: {
    toggleDone: function (todo) {
      todo.done = !todo.done
    },
    addNew: function () {
      this.todos.push({value: this.newTodo, done: false})
      this.newTodo = ''
    }
  },
  watch: {
    todos: {
      handler: function (todo) {
        Store.save(todo)
        // console.log(value, oldValue)
      },
      deep: true
    }
  }
}
</script>


<style scoped>
.done{
  text-decoration: underline;
}
</style>
