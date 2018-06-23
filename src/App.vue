<template>
  <div id="app">
    <todoList v-bind:todos="todos"/>
    <createTodo v-on:add-todo="addTodo" />
  </div>
</template>

<script>
import todoList from './components/todoList';
import createTodo from './components/createTodo';


export default {
  name: 'App',
  components: {
    todoList,
    createTodo,
  },
  data(){
    return{
      todos:[
        {
          title: 'Todo A',
          project: 'Project A',
          done: false
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: true
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: false
        },
        {
          title: 'Todo D',
          project: 'Project D',
          done: false
        },
      ],
    };
  },
  methods: {
    addTodo(title){
      this.todo.push({
        title,
        done: false,
      });
    },
  },
};
</script>

<style>

</style>
