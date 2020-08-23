<template>
  <li class="list-item" :id="index">
    <div class="order-container">
      <div class="order-display" v-if="isRandomized">{{index + 1}}</div>
    </div>
    {{item.item}}
    <b-icon icon="backspace" @click="onDelete"></b-icon>
  </li>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    item: Object,
    index: Number,
    isRandomized: Boolean,
  },
  data: function () {
    return {};
  },
  methods: {
    onDelete: function () {
      this.$emit("onDelete", this.index);
    },
  },
};
</script>

<style lang="scss" scoped>
.list-item {
  list-style: none;
  margin: 5px 0;
  padding: 10px 0;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  align-items: center;

  &:not(:last-child) {
    border-bottom: 1px solid rgb(221, 221, 221);
  }

  .order-container {
    justify-self: flex-start;
  }

  .b-icon {
    justify-self: flex-end;
    font-size: 1.5rem;

    &:hover {
      fill: red;
      cursor: pointer;
      transition: fill 0.5s;
    }
  }
}
</style>