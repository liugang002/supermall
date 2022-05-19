<template>
  <div class="goodslistitem">
    <img :src="goodsItem.show.img" alt="" />
    <div class="goodsinfo">
      <p class="gtitle">{{ goodsItem.title }}</p>
      <div class="gdetail">
        <span class="price">{{ goodsItem.price }}</span>
        <span>&nbsp;❤</span>
        <span class="collect">{{ goodsItem.cfav }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {};
      },
    },
  },
};
</script>

<style scoped>
.goodslistitem {
  display: flex;
  flex-direction: column;
  width: 40%;
  justify-content: space-between;
  padding-bottom: 5px;
}
.goodslistitem img{
    border-radius: 5px;
}
/* .price{
    margin: auto;
} */
.gtitle {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.goodsinfo {
  display: flex;
  flex-direction: column;
}
.gdetail {
  align-self: center;
}
.price{
    color:pink;
    /* margin-left: 0px; */
}
</style>
