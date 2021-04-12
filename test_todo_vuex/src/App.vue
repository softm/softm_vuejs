<template>
  <div id="app">
    <h1 class="text-center">Todo App</h1>
    <CompletedTodo :todos="todos" />
    <AddTodo @add-todo="addTodo"/>
    <hr>
    <TodoList 
      :todos="todos"
      @toggle-checkbox="toggleCheckbox"
      @click-delete="deleteTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue';
import AddTodo from '@/components/AddTodo.vue';
import CompletedTodo from '@/components/CompletedTodo.vue';
export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo,
    CompletedTodo
  },
  data() {
    return {
        todos:[
          {id : 1, text: 'bur a car', checked:false},
          {id : 2, text: 'bur a cylce', checked:false},
        ],
        todoText:""
    }
  },
  methods:{
    deleteTodo(id){
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos.splice(index,1);
    },
    addTodo(value) {
      console.log(value);
      this.todos.push({
        id:Math.random(),
        text:value,
        checked:false,
      });
    },
    toggleCheckbox({id, checked}){
      console.log(id, checked);
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos[index].checked = checked;
    }
  }
}
</script>

<style>
</style>
