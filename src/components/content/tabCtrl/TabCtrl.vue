<template>
  <div class="tab-ctrl">
    <div v-for="(item, index) in titles" :key="index" class="tab-ctrl-item">
      <span :class="{active: index === currentIndex}" @click="spanClick(index)">{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabCtrl",
  data() {
    return {
      currentIndex: 0,
    }
  },
  props: {
    titles: {
      type: Array,
      default() {
        return []
      }
    }
  },
  methods: {
    spanClick(index) {
      this.currentIndex = index
    }
  },
}
</script>

<style>
  .tab-ctrl{
    display: flex;
    text-align: center;
    font-size: 15px;
    background-color: #fff;
    z-index: 9;
  }
  .tab-ctrl-item{
    flex: 1;
    height: 40px;
    line-height: 40px;
  }
  .tab-ctrl-item span {
    padding: 5px;
  }
  .active{
    color: var(--color-high-text);
    border-bottom: 2px solid var(--color-high-text);
  }
</style>