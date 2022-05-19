<template>
  <div class="goods">
    <goods-list-item-vue v-for="(item,index) in goods" :key="index" :goodsItem="item">
    
    </goods-list-item-vue>
  </div>
</template>

<script>
import GoodsListItemVue from "./GoodsListItem.vue";

export default {
  components: {
      GoodsListItemVue
  },
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style scoped>
.goods{
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
