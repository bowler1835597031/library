<template>
  <div>
    <headerBooks @search="search"></headerBooks>
    <containBooks :books="bookview" @find="find" @del="del"></containBooks>
    <addBooks @addbook="addbook"></addBooks>
  </div>
</template>

<script>
import headerBooks from './components/headerBooks.vue';
import containBooks from './components/containBooks.vue';
import addBooks from './components/addBooks.vue';

export default {
  components: {
    headerBooks,
    containBooks,
    addBooks,
  },
  data() {
    return {
      isDisabled: false,
      status: 'view', //'serach','addview'
      books: [],
      book: [],
    };
  },
  created() {
    this.$axios({
      url: '/api/getbooks',
    }).then((res) => {
      console.log(res);
      this.books = res.data.data;
    });
  },
  computed: {
    bookview() {
      if (this.status == 'view') {
        return this.books;
      } else if (this.status == 'search') {
        return this.book;
      }
    },
  },
  methods: {
    del(id) {
      this.$axios({
        url: '/api/delbook',
        params: { id },
      }).then((res) => {
        alert(res.data.msg);
      });
    },
    find(id) {
      this.$axios({
        url: '/api/getbooks',
        params: {
          id,
        },
      }).then((res) => {
        alert(JSON.stringify(res.data.data));
      });
    },
    search(bookname) {
      this.$axios({
        url: '/api/getbooks',
        params: {
          bookname: bookname,
        },
      }).then((res) => {
        console.log(res);
        this.book = res.data.data;
      });
      this.status = 'search';
    },
    addbook(bookobj) {
      this.$axios({
        url: '/api/addbook',
        method: 'POST',
        data: {
          ...bookobj,
        },
      }).then((res) => {
        console.log(res);
        alert(res.data.msg);
      });
    },
  },
};
</script>

<style></style>
