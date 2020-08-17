<template>
  <div>
    <input type="text" class="todo-input" placeholder="What needs to be done" v-model="newTodo"/>
    Todo List goes here
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      msg: "Welcome to Your TodoList App",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">

.todo-input{
  width: 100%;
  padding: 10px 18px;
  margin-bottom: 20px;
  font-size: 18px;
  &:focus{
    outline: 0;
  }
}

</style>  
