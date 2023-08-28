<template>
    <div id="app">
      <to-do-list></to-do-list>
    </div>
  </template>
  <script>
  import ToDoList from './first.vue';
  
  export default {
    components: {
      ToDoList
    }
  };
  </script>
  
  <style scoped>
    *{
        display: flex;
        justify-content: center;
        margin-top: 50px;
        font-family: Verdana, Arial, Helvetica, sans-serif;
    }
  </style>
  <style>
    body {
      background: rgb(63,94,251);
      background: linear-gradient(90deg, rgba(63,94,251,1) 0%, rgba(252,70,107,1) 100%);
    }
  </style>
  
  