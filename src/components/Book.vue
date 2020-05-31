<template>
  <div class="img-container">
    <a :href="item.linkUrl" rel="noreferrer" target="_blank">
      <img :src="item.imgUrl" :alt="item.alt" />
    </a>
  </div>
</template>

<script>
export default {
  name: "Book",
  props: {
    item: Object
  }
};
</script>

<style scoped>
.img-container {
  position: relative;
  width: 150px;
  height: 300px;
  max-height: 170px;
  overflow: hidden;
  margin: 1rem;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
}
img {
  position: absolute;
  max-width: 100%;
  width: 100%;
  height: auto;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
