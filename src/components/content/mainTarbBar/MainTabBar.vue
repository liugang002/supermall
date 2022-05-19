<template>
  <tab-bar>
    <tab-bar-item-vue path="/home" activeColor="">
      <template v-slot:item-icon>
        <img src="~assets/img/tabbar/home.svg" alt="" />
      </template>
      <template v-slot:item-active>
        <img src="~assets/img/tabbar/home_active.svg" alt="" />
      </template>
      <template v-slot:item-text>
        <div>首页</div>
      </template>
    </tab-bar-item-vue>
    <tab-bar-item-vue path="/category" activeColor="">
      <template v-slot:item-icon>
        <img src="~assets/img/tabbar/category.svg" alt="" />
      </template>
      <template v-slot:item-active>
        <img src="~assets/img/tabbar/category_active.svg" alt="" />
      </template>
      <template v-slot:item-text>
        <div>分类</div>
      </template>
    </tab-bar-item-vue>
    <tab-bar-item-vue path="/cart" activeColor="">
      <template v-slot:item-icon>
        <img src="~assets/img/tabbar/shopcart.svg" alt="" />
      </template>
      <template v-slot:item-active>
        <img src="~assets/img/tabbar/shopcart_active.svg" alt="" />
      </template>
      <template v-slot:item-text>
        <div>购物车</div>
      </template>
    </tab-bar-item-vue>
    <tab-bar-item-vue path="/profile" activeColor="">
      <template v-slot:item-icon>
        <img src="~assets/img/tabbar/profile.svg" alt="" />
      </template>
      <template v-slot:item-active>
        <img src="~assets/img/tabbar/profile_active.svg" alt="" />
      </template>
      <template v-slot:item-text>
        <div>我的</div>
      </template>
    </tab-bar-item-vue>
  </tab-bar>
</template>

<script>
import TabBar from "components/common/tabbar/TabBar.vue";
import TabBarItemVue from "components/common/tabbar/TabBarItem.vue";
export default {
  components: {
    TabBarItemVue,
    TabBar,
  },
};
</script>

<style></style>
