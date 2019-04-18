<template>
  <div>
      <div class="page-banner">
        <MyCarousel :dataList="bannerList"></MyCarousel>
      </div>
  </div>
</template>

<script>
import MyCarousel from '#/MyCarousel';

export default {
  name: 'Home',
  data () {
    return {
      bannerList: []
    }
  },
  components: {MyCarousel},
  methods: {
    init() {
      this.bannerList = [
        {
          bgColor: '#f6ede4',
          url: require('../assets/image/banner1.jpg')
        }, {
          bgColor: '#2a1842',
          url: require('../assets/image/banner2.jpg')
        }, {
          bgColor: '#80d3e1',
          url: require('../assets/image/banner3.jpg')
        }, {
          bgColor: '#b5e2ff',
          url: require('../assets/image/banner4.jpg')
        }, {
          bgColor: '#feeaf3',
          url: require('../assets/image/banner5.jpg')
        }
      ]
    }
  },
  created() {
    this.init();
  }
}
</script>

<style lang="scss" scoped>
  .page-banner {
    // background: #2a1842;
    height: 400px;
    min-width: 990px;
  }
</style>
