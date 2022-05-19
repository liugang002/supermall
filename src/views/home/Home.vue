<template>
  <div id="home">
    <nav-bar-vue class="home-nav">
      <template v-slot:center>
        <h2>购物街</h2>
      </template>
    </nav-bar-vue>
    <scroll-vue
      :probe-type="3"
      @scroll="contentScroll"
      class="content"
      ref="scroll"
      :pull-up-load="true"
      @pullingUp="loadMore"
    >
      <recommend-view-vue :recommends="recommends"></recommend-view-vue>
      <feature-vue></feature-vue>
      <tab-control-vue
        @tabClick="tabClick"
        class="tab-control"
        :titles="['流行', '新款', '精选']"
      ></tab-control-vue>
      <good-list :goods="showGoods"></good-list>
    </scroll-vue>
    <back-top-vue v-show="isShowBackTop" @click.native="backClick"></back-top-vue>
    <!-- <banner-vue  :oldbanners="banners" ></banner-vue> -->
  </div>
</template>

<script>
// import BannerVue from "@/components/common/banner/Banner.vue";
import RecommendViewVue from "./childComps/RecommendView.vue";
import FeatureVue from "./childComps/Feature.vue";
import TabControlVue from "@/components/content/tabControl/TabControl.vue";
import GoodList from "@/components/content/goods/GoodList.vue";

import NavBarVue from "@/components/common/navbar/NavBar.vue";
import ScrollVue from "@/components/common/scroll/Scroll.vue";
import BackTopVue from "@/components/content/backTop/BackTop.vue";

import { getHomeMultidata, getHomeGoods } from "@/network/home";
export default {
  name: "Home",
  components: {
    NavBarVue,
    // BannerVue,
    RecommendViewVue,
    FeatureVue,
    TabControlVue,
    GoodList,
    ScrollVue,
    BackTopVue,
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
      currentType: "pop",
      isShowBackTop:false
    };
  },
  created() {
    //1.请求多个数据
    this.getHomeMultidata();
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
  computed: {
    showGoods() {
      return this.goods[this.currentType].list;
    },
  },
  methods: {
    /**
     * 事件监听相关方法
     */

    tabClick(index) {
      console.log(index);

      this.currentType = Object.entries(this.goods)[index][0];
    },
    contentScroll(position) {
      this.isShowBackTop = Math.abs(position.y) > 1000
    },
    loadMore(){
      this.getHomeGoods(this.currentType)
      this.$refs.scroll.finishPullUp();
      this.$refs.scroll.scroll.refresh();
    },
    /**
     * 网络请求相关方法
     */
    getHomeMultidata() {
      getHomeMultidata().then((res) => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then((res) => {
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page = page;
      });
    },
    backClick() {
      this.$refs.scroll.scrollTo(0, 0, 500);
    },
  },
};
</script>

<style scoped>
#home {
  /* padding-top: 44px; */
  height: 100vh;
}
.home-nav {
  background-color: var(--color-tint);
  color: aliceblue;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
}

.tab-control {
  position: sticky;
  top: 44px;
}

.content {
  margin-top: 44px;
  height: calc(100% - 93px);
  overflow: hidden;
}
</style>
