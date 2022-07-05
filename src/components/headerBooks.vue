<template>
  <div id="headerBooks" class="in">
    <input
      type="text"
      placeholder="搜索-书本名称"
      v-model.trim="bookname"
      @keydown.enter="search"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      bookname: '',
    };
  },
  methods: {
    search() {
      if (this.bookname.length == 0) {
        return alert('bookname is empty');
      }
      this.$emit('search', this.bookname);
      this.bookname = '';
    },
  },
};
</script>

<style>
.in {
  padding-left: 50px;
}
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
</style>
