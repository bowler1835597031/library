<template>
  <div class="in">
    <table class="tab">
      <tr>
        <th>序号</th>
        <th>书名</th>
        <th>作者</th>
        <th>出版社</th>
        <th>操作</th>
      </tr>
      <tr v-for="item in books" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.bookname }}</td>
        <td>{{ item.author }}</td>
        <td>{{ item.publisher }}</td>
        <td>
          <a href="javascript:;" @click="del(item.id)">删除</a>
          <a href="javascript:;" @click="find(item.id)">详情</a>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    books: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {};
  },
  methods: {
    find(id) {
      this.$emit('find', id);
    },
    del(id) {
      this.$emit('del', id);
    },
  },
};
</script>

<style>
.in {
  padding-left: 50px;
}
.tab {
  width: 800px;
  /* height: 500px; */
  border: 1px solid #dde0e6;
}
th {
  border: 1px solid #dde0e6;
  border-bottom: 2px solid #000000;
  text-align: start;
  padding: 5px 0 5px 5px;
}
td {
  border: 1px solid #dde0e6;
  padding: 5px 0 5px 5px;
}
.tab,
th,
td {
  border-collapse: collapse;
}
</style>
