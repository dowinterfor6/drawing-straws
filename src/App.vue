<template>
  <div id="app">
    <h1>Drawing Straws</h1>
    <List />
  </div>
</template>

<script>
import List from "./components/List";

export default {
  name: "App",
  components: {
    List,
  },
};
</script>

<style lang="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  border: 1px solid rgb(148, 148, 148);
  border-radius: 5px;
  margin: 10% auto;
  padding: 20px;
  width: 80%;

  @media only screen and (min-width: 768px) {
    margin: 100px auto;
    width: 500px;
  }

  h1 {
    margin: 10px 0;
  }
}
</style>
