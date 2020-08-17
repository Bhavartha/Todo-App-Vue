<template>
  <div>
    <input
      type="text"
      class="todo-input"
      placeholder="What needs to be done"
      v-model="newTodo"
      @keyup.enter="addTodo"
    />
    <div v-for="(todo,index) in todos" :key="todo.id" class="todo-item">
      <div>{{ todo.title }}</div>
      <div class="remove-item" @click="removeTodo(index)" >&times;</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      newTodo: "",
      idForTodo: 3,
      todos: [
        {
          id: 1,
          title: "Finish Electron Recorder",
          completed: false,
        },
        {
          id: 2,
          title: "Make Tailwind App",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (!this.newTodo.trim().length) return;

      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
      });
      this.newTodo = "";
      this.idForTodo++;
    },

    removeTodo(index){
      this.todos.splice(index,1);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.todo-input {
  width: 100%;
  padding: 10px 18px;
  margin-bottom: 20px;
  font-size: 18px;
  
  &:focus {
    outline: 0;
  }
}

.todo-item {
  display: flex;
  margin-bottom: 15px;
  align-items: center;
  justify-content: space-between;
}

.remove-item {
  cursor: pointer;
  padding:0 7px;
  &:hover {
    font-weight: bold;
  }
}
</style>  
