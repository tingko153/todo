<template>
    <li>
        <input type="checkbox" v-model="item.complete" :value='item.no' />

        <input v-if="isModify" type="text" v-model='item.name' @keyup.enter="modify" />
        <span v-else>{{item.name}}</span>

        <a href="#" @click='modify'>수정</a>
        <a href="#" @click='deleteItem(item.no)'>삭제</a>
    </li>
</template>

<script>
export default {
  name: 'Item',
  props: [ 'item' ],
  data() {
      return {
          isModify: false
      }
  },
  methods: {
      modify() {
          this.isModify = !this.isModify;
      },
      deleteItem(n) {
          this.$emit('deleteItem', n);
      }
  }
}
</script>

