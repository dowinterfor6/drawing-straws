<template>
  <section class="list">
    <b-button @click="handleRandomize" variant="success">Randomize</b-button>
    <form @submit="onSubmit" class="input-container">
      <b-form-input v-model="newItem"></b-form-input>
      <b-form-text>Press enter to add to list</b-form-text>
    </form>
    <transition-group class="list-item-container" name="list-item-container" tag="ul">
      <ListItem
        v-for="(item, index) in listData"
        :key="item.key"
        :item="item"
        :index="index"
        :isRandomized="isRandomized"
        @onDelete="handleDelete"
      />
    </transition-group>
  </section>
</template>

<script>
import ListItem from "./ListItem";
import _ from "lodash";

export default {
  name: "List",
  components: {
    ListItem,
  },
  data: function () {
    return {
      newItem: "",
      listData: [],
      isRandomized: false,
    };
  },
  methods: {
    onSubmit: function (e) {
      e.preventDefault();
      if (this.newItem) {
        const currIndex = this.listData.length + 1;
        this.listData.push({
          item: this.newItem,
          key: `${this.newItem}-${currIndex}`,
        });
        this.newItem = "";
      }
    },
    handleDelete: function (index) {
      this.listData.splice(index, 1);
    },
    handleRandomize: function () {
      this.isRandomized = true;
      this.listData = _.shuffle(this.listData);
    },
  },
};
</script>

<style lang="scss">
.list {
  .btn {
    margin-bottom: 10px;
  }

  .input-container {
    margin-bottom: 20px;
  }

  .list-item-container {
    &-move {
      transition: transform 1s;
    }
    padding-left: 0;
    margin-bottom: 0;
  }
}
</style>
