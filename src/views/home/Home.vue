<template>
  <div id="home">
    <nav-bar class="home-nav"><template slot="center"><div>购物街</div></template>
    </nav-bar>
    <swiper>
      <swiper-item v-for="(item,index) in banners" :key="index">
        <a :href="item.link">
          <img :src="item.image" alt="">
        </a>
      </swiper-item>
    </swiper>
    <home-recommend :recommends="recommends"/>
  </div>
</template>

<script>
import NavBar from 'components/commen/navbar/NavBar';
import {Swiper, SwiperItem} from 'components/commen/swiper';
import HomeRecommend from './childrenComps/HomeRecommend';
import {getHomeMultidata} from '../../network/home';
export default {
  name:"Home",
  data() {
    return {
      banners: [],
      recommends:[],
    }
  },
  components:{
    NavBar,
    Swiper,
    SwiperItem,
    HomeRecommend
  },
  created() {
    //1.请求多个数据
    getHomeMultidata().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
  },

}
</script>

<style>
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
  }
</style>