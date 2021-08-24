<template>
  <div>

    <div>
      <p>タイトル：<input type="text" v-model="title"></p>
      <p>著者：<input type="text" v-model="author"></p>
      <button @click="addBook">追加</button>
    </div>

    <div>
      <ul>
        <li v-for="book in books" :key="book.id">
          {{ book.id }} / {{ book.title }} / {{ book.author }}
          <button
            :disabled="isPush"
            @click="displayUpdate(book)"
          >編集</button>
          <button
            :disabled="isPush" @click="deleteBook(book.id)"
          >削除</button>
        </li>
      </ul>
    </div>

    <div v-if="updateForm">
      <p>ID：{{ updateId }}</p>
      <p>タイトル：<input type="text" v-model="updateTitle"></p>
      <p>著者：<input type="text" v-model="updateAuthor"></p>
      <button @click="updateBook()">追加</button>
      <button @click="updateCancel">キャンセル</button>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      books: {},
      title:'',
      author: '',
      isPush: false,
      updateForm: false,
      updateId: '',
      updateTitle: '',
      updateAuthor: '',
    }
  },
  created() {
    this.getBooks();
  },
  methods: {
    getBooks() {
      axios.get('/api/books').then(res => {
        this.books = res.data;
      });
    },
    addBook() {
      axios.post('/api/books/', {
        title: this.title,
        author: this.author
      }).then(() => {
        this.title = '',
        this.author = ''
        this.getBooks();
      });
    },
    displayUpdate(book) {
      this.isPush = true;
      this.updateForm = true;
      this.updateId = book.id;
      this.updateTitle = book.title;
      this.updateAuthor = book.author;
    },
    updateBook() {
      axios.put('/api/books/' + this.updateId, {
        title: this.updateTitle,
        author: this.updateAuthor
      }).then(() => {
        this.isPush = false;
        this.updateForm = false;
        this.getBooks();
      });
    },
    updateCancel() {
      this.isPush = false;
      this.updateForm = false;
    },
    deleteBook(id) {
      axios.delete('/api/books/' + id).then(() => {
        this.getBooks();
      });
    },
  },
}
</script>