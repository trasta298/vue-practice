<template>
  <div>
    <h1>Todo List</h1>
    <item-list/>
  </div>
</template>

<script>
import ItemList from "./ItemList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    ItemList
  }
};
</script>