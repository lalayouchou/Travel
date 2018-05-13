<template>
  <div>
    <div class="item border-bottom"
    v-for="(item, index) of list"
    :key="index"
    >{{item.title}}
      <div class="children" v-if="item.children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
.item
  line-height .6rem
  padding 0 .2rem
</style>
