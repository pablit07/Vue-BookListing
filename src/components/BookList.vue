<template>
<div>
  <h1> {{ title }}</h1>
  <ul>
    <book-item v-for="book in books" :book="book" :key="book.title.split('').reduce((h, ch) => (((h<<5)-h)+ch.charCodeAt(0)), '')">
    </book-item>
  </ul>
  <book-form @addBook='appendBook'></book-form>
</div>
</template>

<script>
import BookItem from './BookItem';
import BookForm from './BookForm';
export default {
  name: 'BookList',
  components: { BookItem, BookForm },
  data: () => ({
    title: "All Books",
    books:[
      {title: 'Self-Reliance', author: 'Ralph Waldo Emerson'},
      {title: 'American Gods', author: 'Neil Gaiman'},
      {title: 'Amusing Ourselves to Death', author: 'Neil Postman'},
    ]
  }),
  methods: {
    appendBook(bookTitle, bookAuthor) {
      this.books.push({ title: bookTitle, author: bookAuthor })
    }
  }
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
