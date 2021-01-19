<template>
<div>
  <h1> {{ title }}</h1>
  <ul>
    <book-item v-for="book in books" :book="book" :key="book.title.split('').reduce((hash, char) => (((hash<<5)-hash)+char.charCodeAt(0)), '')">
    </book-item>
  </ul>
</div>
</template>

<script>
import BookItem from './BookItem';
export default {
  name: 'BookList',
  components: { BookItem },
  data: () => ({
    title: "All Books",
    books:[
      {title: 'Self-Reliance', author: 'Ralph Waldo Emerson'},
      {title: 'American Gods', author: 'Neil Gaiman'},
      {title: 'Amusing Ourselves to Death', author: 'Neil Postman'},
    ]
  })
};
</script>

<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0
  }
</style>
