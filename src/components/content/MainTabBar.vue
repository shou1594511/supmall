<template>
  <tab-bar>
      <tab-bar-item path="/home" activeColor="">
        <img src="~assets/image/tabbar/home.svg" alt="" slot="item-icon">
        <img src="~assets/image/tabbar/home_active.svg" alt="" slot="item-active">
        <div slot="item-name">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/category" activeColor="">
        <img src="~assets/image/tabbar/category.svg" alt="" slot="item-icon">
        <img src="~assets/image/tabbar/category_active.svg" alt="" slot="item-active">
        <div slot="item-name">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/cart" activeColor="">
        <img src="~assets/image/tabbar/shopcart.svg" alt="" slot="item-icon">
        <img src="~assets/image/tabbar/shopcart_active.svg" alt="" slot="item-active">
        <div slot="item-name">购物车</div>
      </tab-bar-item>
      <tab-bar-item path="/profile" activeColor="">
        <img src="~assets/image/tabbar/profile.svg" alt="" slot="item-icon">
        <img src="~assets/image/tabbar/profile_active.svg" alt="" slot="item-active">
        <div slot="item-name">我的</div>
      </tab-bar-item>
    </tab-bar>
</template>

<script>
import TabBar from 'components/commen/tabbar/TabBar';
import TabBarItem from 'components/commen/tabbar/TabBarItem';
export default {
  name:"MainTabBar",
  components:{
    TabBar,
    TabBarItem
  }
}
</script>

<style>

</style>