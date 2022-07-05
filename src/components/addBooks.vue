<template>
  <div id="addBooks">
    <input
      type="text"
      name=""
      id=""
      placeholder="书名"
      v-model="bookobj.bookname"
    />
    <br />
    <input
      type="text"
      name=""
      id=""
      placeholder="作者"
      v-model="bookobj.author"
    />
    <br />
    <input
      type="text"
      name=""
      id=""
      placeholder="出版社"
      v-model="bookobj.publisher"
    />
    <br />
    <button @click="addbook" :style="{ disabled: isDiabled }">新增</button>
  </div>
</template>

<script>
export default {
  props: ['isDiabled'],
  data() {
    return {
      bookobj: {
        bookname: '',
        author: '',
        publisher: '',
      },
    };
  },
  methods: {
    addbook() {
      this.$emit('addbook', this.bookobj);
      this.bookobj.bookname = '';
      this.bookobj.author = '';
      this.bookobj.publisher = '';
    },
  },
};
</script>

<style>
input {
  margin-bottom: 10px;
  height: 20px;
  border: 1px solid #c5ccd3;
  border-radius: 3px;
  color: #757575;
  font-size: 12px;
}
input::placeholder {
  padding-left: 10px;
}
#Bottom {
  margin-top: 10px;
}
#Bottom input {
  margin-bottom: 15px;
}
#Bottom button {
  width: 60px;
  height: 30px;
  border: 0 solid;
  border-radius: 5px;
  font-size: 15px;
  background-color: #0b6dfd;
  color: #ffffff;
}
</style>
