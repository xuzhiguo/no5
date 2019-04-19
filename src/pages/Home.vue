<template>
  <div class="page">
      <div class="page-banner">
        <MyCarousel :dataList="bannerList"></MyCarousel>
      </div>
      <div class="page-menu">
        <div class="menu-box">
          <div class="menu">
            <div class="menu-item" v-for="(item,idx) in menuList" :key="idx" :class="{'active': item.showDetail}">
              <div class="title">
                <h5>{{item.kind}}</h5>
                <span></span>
              </div>
              <div class="list">
                <span :class="{'hot': one.hot}" v-for="(one,key) in item.list" :key="key">{{one.name}}</span>
              </div>
              <ul class="detail-list" v-show="item.showDetail">
                <li>
                  <div class="detail-title"></div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="page-image-box">
        <div class="content">
          <div class="boardcast">
            <span></span>
            情人节礼物就送口红，你的女神肯定喜欢！！！
          </div>
          <div class="image-list">
            <img v-for="(item,idx) in boardcastImageList" :key="idx" :src="item.url" alt="">
          </div>
        </div>
      </div>
      <div class="page-limtbuy">
        <div class="content">
          <h5>
            <img src="../assets/image/qianggou.jpg" alt="限时抢购">
          </h5>
        </div>
      </div>
  </div>
</template>

<script>
import MyCarousel from '#/MyCarousel';

export default {
  name: 'Home',
  data () {
    return {
      bannerList: [],
      menuList: [],
      boardcastImageList: []
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
      ];

      this.menuList = [
        {
          kind: '面部护理',
          showDetail: false,
          list: [
            {name: '洗面奶', hot: false },
            {name: '爽肤水', hot: false },
            {name: '乳液', hot: false },
            {name: '防晒', hot: false },
            {name: '面膜', hot: false },
            {name: '精华', hot: true },
            {name: '眼霜', hot: false },
            {name: '卸妆', hot: false },
            {name: 'T区护理', hot: false }
          ],
          detail: [
            {
              name: ''
            }
          ]
        }, {
          kind: '彩妆',
          showDetail: false,
          list: [
            {name: 'BB霜', hot: false },
            {name: '粉底液', hot: false },
            {name: '妆前乳', hot: false },
            {name: '隔离', hot: false },
            {name: '唇膏', hot: true },
            {name: '睫毛膏', hot: false },
            {name: '眼线', hot: false },
            {name: '指甲油', hot: false }
          ]
        }, {
          kind: '香氛',
          showDetail: false,
          list: [
            {name: '女士香水', hot: false },
            {name: '男士香水', hot: false },
            {name: '香水套装', hot: true },
            {name: '中性香水', hot: false },
            {name: '限量版', hot: false }
          ]
        }, {
          kind: '身体护理',
          showDetail: false,
          list: [
            {name: '香皂', hot: false },
            {name: '沐浴露', hot: false },
            {name: '身体乳', hot: true },
            {name: '瘦身霜', hot: false },
            {name: '脱毛膏', hot: false },
            {name: '美胸霜', hot: false },
            {name: '颈霜', hot: false },
            {name: '护手霜', hot: true }
          ]
        }, {
          kind: '头发护理',
          showDetail: false,
          list: [
            {name: '洗发水', hot: false },
            {name: '护发素', hot: false },
            {name: '发膜', hot: true },
            {name: '修护精华', hot: false },
            {name: '防脱发', hot: false },
            {name: '染发', hot: false },
            {name: '套装', hot: false }
          ]
        }, {
          kind: '男士专区',
          showDetail: false,
          list: [
            {name: '面部护肤', hot: true },
            {name: '男士防晒', hot: false },
            {name: '剃须护理', hot: false },
            {name: '洗发护发', hot: false },
            {name: '沐浴止汗', hot: false },
            {name: '男士精品', hot: false }
          ]
        }, {
          kind: '美容工具',
          showDetail: false,
          list: [
            {name: '化妆包', hot: false },
            {name: '购物袋', hot: false },
            {name: '化妆刷', hot: false },
            {name: '彩妆工具', hot: false },
            {name: '护肤工具', hot: false },
            {name: '美体工具', hot: false }
          ]
        }
      ];

      this.boardcastImageList = [
        {
          url: require('../assets/image/image1.jpg'),
          router: ''
        }, {
          url: require('../assets/image/image2.jpg'),
          router: ''
        }, {
          url: require('../assets/image/image3.jpg'),
          router: ''
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
  @import '../assets/style/index';

  .page {
    position: relative;
  }

  .page-banner {
    // background: #2a1842;
    height: 400px;
    min-width: 990px;
  }

  .page-menu {
    position: absolute;
    top: 0;
    width: 100%;
    height: 400px;
    margin: 0 auto;
    .menu-box {
      width: 1200px;
      height: 100%;
      margin: 0 auto;
      .menu {
        width: 224px;
        background: #f8f8f8;
        .menu-item {
          position: relative;
          padding: 20px 16px 8px;
          border-bottom: solid 1px #e7e7e7;
          border-right: solid 1px #e7e7e7;
          .title {
            display: flex;
            width: 100%;
            justify-content: space-between;
            align-items: center;
            h5 {
              font-size: .85rem;
              color: #333333;
            }
            span {
              display: block;
              width: 6px;
              height: 9px;
              background: url('../assets/image/detail.gif') no-repeat -310px -30px;
            }
          }
          .list {
            display: flex;
            flex-wrap: wrap;
            span {
              display: block;
              padding: 5px 10px 0 0;
              color: #666;
              &.hot {
                color: $hot;
              }
            }
          }
          .detail-list {
            position: absolute;
            left: 224px;
            top: 0;
            padding: 0 20px;
            border: 1px solid #bdbdbd;
            .detail-title {

            }
          }
          &.active {
            background: #fff;
            border-right: none;
            border-bottom: 1px solid #bdbdbd;
            border-left: solid 2px #00adff;
          }
        }
      }
    }
  }

  .page-image-box {
    .content {
      width: 1200px;
      margin: 0 auto;
      padding-left: 224px;
      .boardcast {
        display: flex;
        align-items: center;
        padding: 5px 10px;
        color: #666;
        span {
          width: 19px;
          height: 19px;
          margin-right: 6px;
          background: url('../assets/image/detail.gif') no-repeat -409px -30px;
        }
      }
      .image-list {
        padding-left: 10px;
        img {
          margin-right: 10px;
          width: 313px;
          height: 187px;
          &:last-of-type {
            margin: 0;
          }
        } 
      }
    }
  }

  .page-limtbuy {
    .content {
      width: 1200px;
      margin: 0 auto;
      border-bottom: 1px solid #e4e4e4;
      h5 {
        border-bottom: 2px solid #ff8c8f;
        padding: 30px 0 8px 2px;
        margin-bottom: 10px;
        img {
          height: 24px;
        } 
      }
    }
  }
</style>
