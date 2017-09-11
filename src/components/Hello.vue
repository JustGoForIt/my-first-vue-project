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
export default {
  name: 'hello',
  data () {
    return {
      title: 'this is a vue-todolist',
      todos: [
        // {value: '阅读一本关于前端开发的书', done: false},
        // {value: '补充范例代码', done: true},
        // {value: '写心得', done: false},
        // {value: '写博客', done: false}
      ],
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
      Store.save()
    }
  },
  watch:{
    items:{
      handler: function(){

      },
      deep
    }
  }
}
</script>


<style scoped>
.done{
  text-decoration: underline;
}
</style>
