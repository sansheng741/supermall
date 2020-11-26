<template>
  <div id="home">
    <nav-bar class="home-nav-bar">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"/>
    <recommend-view :recommends="recommend"/>
    <feature-view/>
    <tab-control :title="['流行', '新款', '精选']"/>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import {getHomeMultiData, getHomeGoods} from "@/network/home";
import HomeSwiper from "@/views/home/chridencomps/HomeSwiper";
import RecommendView from "@/views/home/chridencomps/RecommendView";
import FeatureView from "@/views/home/chridencomps/FeatureView";
import TabControl from "@/components/content/tabControl/TabControl";


export default {
  name: "Home",
  components: {
    TabControl,
    FeatureView,
    RecommendView,
    NavBar,
    HomeSwiper
  },
  data() {
    return {
      banner: null,
      recommend: null,
      goods: {
        'pop': {page: 0, list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []}
      }
    }
  },
  created() {
    getHomeMultiData().then(res => {
      this.banner = res.data.banner.list
      this.recommend = res.data.recommend.list
      this.dKeyword = res.data.dKeyword.list
      this.keywords = res.data.keywords.list
    })
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods: {
    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
      })
    }

  }
}
</script>

<style scoped>
#home {
  padding-top: 44px;
}

.home-nav-bar {
  background: var(--color-tint);
  color: #fff;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 999;
}
</style>
