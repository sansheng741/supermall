<template>
  <div id="home">
    <nav-bar class="home-nav-bar">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"/>
    <recommend-view :recommends="recommend"/>
    <feature-view/>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import {getHomeMultiData} from "@/network/home";
import HomeSwiper from "@/views/home/chridencomps/HomeSwiper";
import RecommendView from "@/views/home/chridencomps/RecommendView";
import FeatureView from "@/views/home/chridencomps/FeatureView";


export default {
  name: "Home",
  components: {
    FeatureView,
    RecommendView,
    NavBar,
    HomeSwiper
  },
  data() {
    return {
      banner: null,
      recommend: null,
      dKeyword: null,
      keywords: null
    }
  },
  created() {
    getHomeMultiData().then(res => {
      this.banner = res.data.banner.list
      this.recommend = res.data.recommend.list
      this.dKeyword = res.data.dKeyword.list
      this.keywords = res.data.keywords.list
    })
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
