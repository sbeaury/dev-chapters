<template>
  <span
    class="tag"
    v-bind:class="{ 'is-primary': isFilterOn }"
    @click="text !== 'All' ? filterBooks(text) : clearFilter()"
    >{{ text }}</span
  >
</template>

<script>
export default {
  name: "Tag",
  props: {
    text: String,
    filterBooks: Function,
    clearFilter: Function,
    isFilterOn: Boolean,
  },
};
</script>

<style>
.tag {
  cursor: pointer;
}
.tag:not(body) {
  font-size: 1rem !important;
}
</style>
