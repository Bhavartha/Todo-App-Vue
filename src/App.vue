<template>
  <div id="app" class="container">
    <img src="https://image.flaticon.com/icons/svg/748/748646.svg" class="logo" />
    <TodoList />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    HelloWorld,
    TodoList,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

.container {
  max-width: 600px;
  margin: 0 auto;
}

.logo {
  margin: 20px auto;
  height: 75px;
  display: block;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
