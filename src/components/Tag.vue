<template>
  <div
    class="tag is-info is-light"
    @click="text!=='All'? filterBooks(text):clearFilter()"
  >{{ text }}</div>
</template>

<script>
export default {
  name: "Tag",
  props: {
    text: String,
    filterBooks: Function,
    clearFilter: Function
  }
};
</script>

<style>
.tag {
  cursor: pointer;
}
.tag:not(body) {
  font-size: 1rem;
}
</style>