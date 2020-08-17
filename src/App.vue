<template>
  <div id="app" class="container">
    <div class="logo">
      <img src="https://image.flaticon.com/icons/svg/748/748646.svg" />
      <div>TODO</div>
    </div>
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

<style lang="scss">
* {
  box-sizing: border-box;
}

.container {
  max-width: 600px;
  margin: 0 auto;
}

.logo {
  display:flex;
  align-items: flex-end;
  justify-content: center;
  margin: 20px auto;
  img {
    max-width: 80px;
    display: block;
    margin-right: 20px;
  }
  div{
    font-size: 30px;
    font-weight: bolder;
  }
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 18px;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
