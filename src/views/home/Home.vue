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
    <home-feature></home-feature>
    <tab-ctrl :titles="['流行','新款','精选']" class="tab-ctrl"></tab-ctrl>

    <goods-list :goods="goods['pop'].list"></goods-list>
    <ul>
      <li>liebiao1</li>
      <li>liebiao2</li>
      <li>liebiao3</li>
      <li>liebiao4</li>
      <li>liebiao5</li>
      <li>liebiao6</li>
      <li>liebiao7</li>
      <li>liebiao8</li>
      <li>liebiao9</li>
      <li>liebiao10</li>
      <li>liebiao11</li>
      <li>liebiao12</li>
      <li>liebiao13</li>
      <li>liebiao14</li>
      <li>liebiao15</li>
      <li>liebiao16</li>
      <li>liebiao17</li>
      <li>liebiao18</li>
      <li>liebiao19</li>
      <li>liebiao20</li>
      <li>liebiao21</li>
      <li>liebiao22</li>
      <li>liebiao23</li>
      <li>liebiao24</li>
      <li>liebiao25</li>
      <li>liebiao26</li>
      <li>liebiao27</li>
      <li>liebiao28</li>
      <li>liebiao29</li>
      <li>liebiao30</li>
      <li>liebiao31</li>
      <li>liebiao32</li>
      <li>liebiao33</li>
      <li>liebiao34</li>
      <li>liebiao35</li>
      <li>liebiao36</li>
      <li>liebiao37</li>
      <li>liebiao38</li>
      <li>liebiao39</li>
      <li>liebiao40</li>
    </ul>

  </div>
</template>

<script>

import HomeRecommend from './childrenComps/HomeRecommend';
import HomeFeature from './childrenComps/HomeFeature';

import TabCtrl from 'components/content/tabCtrl/TabCtrl';
import NavBar from 'components/commen/navbar/NavBar';
import GoodsList from 'components/content/goods/GoodsList';

import {Swiper, SwiperItem} from 'components/commen/swiper';
import {getHomeMultidata, getHomeGoods} from 'network/home';
export default {
  name:"Home",
  data() {
    return {
      banners: [],
      recommends:[],
      goods: {
        'pop': {page: 0, list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []}
      },
    }
  },
  components:{
    NavBar,
    Swiper,
    SwiperItem,
    HomeRecommend,
    HomeFeature,
    GoodsList,
    TabCtrl
  },
  created() {
    //1.请求多个数据
    this.getHomeMultidata()
    //2.商品数据
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods: {
    getHomeMultidata() {
      getHomeMultidata().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then(res => {
        this.goods[type].list.push(...res.data.list)//es6数组转化
        this.goods[type].page += 1
    })
    }
  },

}
</script>

<style>
  #home {
    padding-top: 44px;
  }
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }
  .tab-ctrl {
    position: sticky;
    top: 44px;
  }
</style>