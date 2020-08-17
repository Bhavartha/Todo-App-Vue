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
      <div class="todo-item-main">
        <input type="checkbox" v-model="todo.completed">
        <div
          class="todo-item-label"
          :class={completed:todo.completed}
          v-if="!todo.editing"
          @dblclick="editTodo(todo)"
        >{{ todo.title }}</div>
        <input
          class="todo-item-edit"
          type="text"
          v-model="todo.title"
          v-else
          v-focus
          @blur="doneTodo(todo)"
          @keyup.enter="doneTodo(todo)"
          @keyup.esc="cancelEdit(todo)"
        />
      </div>
      <div class="remove-item" @click="removeTodo(index)">&times;</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      newTodo: "",
      unedited: "",
      idForTodo: 3,
      todos: [
        {
          id: 1,
          title: "Finish Electron Recorder",
          completed: false,
          editing: false,
        },
        {
          id: 2,
          title: "Make Tailwind App",
          completed: false,
          editing: false,
        },
      ],
    };
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus();
      },
    },
  },
  methods: {
    addTodo() {
      if (!this.newTodo.trim().length) return;

      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
        editing: false,
      });
      this.newTodo = "";
      this.idForTodo++;
    },
    editTodo(todo) {
      this.unedited = todo.title;
      todo.editing = true;
    },
    doneTodo(todo) {
      if (!todo.title.trim().length) {
        todo.title = this.unedited;
      }
      todo.editing = false;
    },
    cancelEdit(todo) {
      todo.editing = false;
      todo.title = this.unedited;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
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
  padding: 0 7px;
  &:hover {
    font-weight: bold;
  }
}

.todo-item-main {
  display: flex;
  align-items: center;
  margin-left: 15px;
}

.todo-item-label {
  padding: 10px;
  border: 1px solid white;
}

.todo-item-edit {
  font-size: 18px;
  padding: 10px;
  width: 100%;
  color: #2c3e50;
  border: 1px solid #ccc;
  &:focus {
    outline: none;
  }
}

.completed{
  text-decoration: line-through;
  color: gray;
}

</style>  
