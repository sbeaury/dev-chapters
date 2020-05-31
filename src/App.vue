<template>
  <div id="app">
    <div class="wrapper">
      <section class="hero">
        <div class="hero-body">
          <div class="container">
            <h1 class="title">Dev Chapters</h1>
            <h2 class="subtitle">Find the best ebooks out there.</h2>
          </div>
        </div>
      </section>
      <div class="level">
        <div class="level-item has-text-centered">
          <div class="tags">
            <Tag text="All" :clearFilter="clearFilter" />
            <Tag v-for="item in tags" :key="item.tag" :text="item.tag" :filterBooks="filterBooks" />
          </div>
        </div>
      </div>
      <div class="shelf">
        <Book v-for="item in books" :key="item.linkUrl" :item="item" />
      </div>
    </div>
    <div class="footer">
      <p>
        {{ copyright }} Built with
        <strong>
          <a href="https://vuejs.org/">Vue</a>
        </strong>.
      </p>
    </div>
  </div>
</template>

<script>
import Book from "./components/Book.vue";
import Tag from "./components/Tag.vue";
import yaml from "js-yaml";
import { BOOKS } from "./data/books.yaml";

export default {
  name: "App",
  components: {
    Book,
    Tag
  },
  data() {
    return {
      books: yaml.load(BOOKS),
      tags: this.removeDuplicates(yaml.load(BOOKS))
    };
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();
      return `© Sébastien Beaury ${currentYear}.`;
    }
  },
  methods: {
    filterBooks(name) {
      this.books = yaml.load(BOOKS);
      this.books = this.books.filter(elt => elt.tag === name);
    },
    clearFilter() {
      this.books = yaml.load(BOOKS);
    },
    removeDuplicates(arrayOfObjects) {
      if (typeof arrayOfObjects !== undefined) {
        return arrayOfObjects.filter(
          (object, index) =>
            index === arrayOfObjects.findIndex(obj => obj.tag === object.tag)
        );
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}

h1 {
  font-family: "Inconsolata", monospace;
}

.shelf {
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -moz-flex;
  display: -webkit-flex;
  display: flex;
  -webkit-flex-direction: row;
  flex-direction: row;
  justify-content: center;
}

.footer {
  background-color: transparent;
  height: 50px;
  margin-top: 50px;
}
</style>
