<script>
export default {
  data() {
    return {
      input: {
        content: '',
        isDone: false,
      },
      todos: [
        {
          content:'Vueをマスターする',
          isDone: true,
        },
        {
          content:'夕飯何にするか決める',
          isDone: false,
        },
        {
          content:'寝る',
          isDone: true,
        },
      ]
    }
  },
  methods:{
    addTodo() {
      if (this.input.content === '') {
        alert('空ですよ')
      }else{
      this.todos.push(this.input)
      this.input = {
        content : '',
        isDone: false
      }
    }
    },
    removeTodo(){
      this.todos = this.todos.filter((todo) =>
        !todo.isDone
      )
    },
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="input.content"/><button @click="addTodo">追加</button><button @click="removeTodo">完了済みを削除する</button>
  <div v-if="todos.length !== 0">
  <ul>
    <li v-for="todo in todos">
      <input type="checkbox" v-model="todo.isDone" /><span v-bind:class="{'todo-done':todo.isDone}">{{todo.content}}</span>
    </li>
  </ul>
</div>
<p v-else>Todoがまだありません！！</p>
</template>

<style>
h1{
  color: "#000"
}

body{
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>