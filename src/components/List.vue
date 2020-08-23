<template>
  <section class="list">
    <b-button variant="success">Randomize</b-button>
    <form @submit="onSubmit" class="input-container">
      <b-form-input v-model="newItem"></b-form-input>
      <b-form-text>Press enter to add to list</b-form-text>
    </form>
    <ul v-for="(item, index) in listData" :key="index">
      <li :id="index">{{item}}</li>
    </ul>
  </section>
</template>

<script>
export default {
  name: "List",
  data: function () {
    return {
      newItem: "",
      listData: [],
    };
  },
  methods: {
    onSubmit: function (e) {
      e.preventDefault();
      console.log("submit");
      if (this.newItem) {
        this.listData.push(this.newItem);
        this.newItem = "";
      }
    },
    deleteItem: function () {},
  },
};
</script>

<style scoped>
</style>
