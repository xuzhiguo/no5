<template>
    <div>
        <div class="header-info">
            <div class="content">
                <div class="left">上午好，欢迎光临No5时尚广场。
                    [<span>登录</span>]
                    [<span>免费注册</span>]
                </div>
                <div class="right">
                    <div class="menu-box" @mouseover="headMenuShow = true" @mouseout="headMenuShow = false">
                        <div class="text">{{headMenuText}}
                            <span></span>
                        </div>
                        <ul class="menu" v-show="headMenuShow">
                            <li v-for="(item,idx) in headMenu" :key="idx" @click="selectHeadMenu(item)">{{item.name}}</li>
                        </ul>
                    </div> |
                    <div class="link">收藏本站</div> |
                    <div class="link">帮助中心</div>
                    <div class="phone">
                        <span></span>
                        010-51666655
                    </div>
                </div>
            </div>
        </div>
        <div class="header-box">
            <div class="content">
                <div class="logo">
                    <img src="../assets/image/logo.jpg" alt="" srcset="">
                </div>
                <div class="query-box">
                    <div class="query-input">
                        <input type="text" value="唇膏">
                        <button>搜索</button>
                    </div>
                    <div class="hot">
                        热门搜索：
                        <span v-for="(item,idx) in hotQueryList" :key="idx" :class="{'more-hot':item.more}">{{item.name}}</span>
                    </div>
                </div>
                <div class="qrcode-box" @mouseover="qrcodeShow = true" @mouseout="qrcodeShow = false">
                    <div class="moblie-menu" v-show="qrcodeShow">
                        <div class="mobile-item">
                            <img src="../assets/image/qrcode-app.png">
                            <div class="info">
                                <h5>app下载</h5>
                                <p>
                                    <a href="http://m.no5.com.cn/DownloadApp" class="android" target="_blank"></a>
                                    <a href="http://itunes.apple.com/cn/app/id1116605773" class="ios" target="_blank"></a>
                                </p>
                            </div>
                        </div>
                        <div class="mobile-item">
                            <img src="../assets/image/qrcode-gzh.jpg">
                            <div class="info">
                                <h5>关注微信公众号</h5>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="shop-car" @mousemove="showCarDetail = true" @mouseout="showCarDetail = false">
                    <div class="car-info">
                        购物车
                        <span>0</span>
                        件
                    </div>
                    <div class="car-detail" v-show="showCarDetail">
                        <div class="empty">
                                购物车中还没有商品，赶紧选购吧！
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="header-nav" id="headerNav" :class="{'top': isFixed}">
            <div class="content">
                <div class="menu">全部商品分类</div>
                <div class="nav">
                    <div class="nav-item" v-for="(item,idx) in headNavList" :key="idx" :class="{'hot': item.hot}">
                        {{item.name}}
                        <span v-show="idx != headNavList.length-1">|</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                headMenuShow: false,
                qrcodeShow: false,
                showCarDetail: false,
                isFixed: false,
                headMenu: [],
                headMenuText: '我的账户',
                hotQueryList: [],
                headNavList: []
            }
        },
        components: {

        },
        methods: {
            init() {
                this.headMenu = [
                    {
                        name: '我的账户',
                        path: 'Account'
                    }, {
                        name: '我的订单',
                        path: 'Order'
                    }, {
                        name: '我的积分',
                        path: 'Credits'
                    }, {
                        name: '我的优惠券',
                        path: 'Discount'
                    }, {
                        name: '我的收藏',
                        path: 'Collect'
                    }
                ];
                this.hotQueryList = [
                    {
                        name: '保湿',
                        more: false
                    }, {
                        name: '防敏感专用',
                        more: true
                    }, {
                        name: '雅诗兰黛',
                        more: false
                    }, {
                        name: '气垫BB',
                        more: false
                    }, {
                        name: '护手霜',
                        more: false
                    }, {
                        name: '专柜小样',
                        more: false
                    }, {
                        name: '口红',
                        more: false
                    },
                ];
                this.headNavList = [
                    {
                        name: '首页',
                        path: '/',
                        hot: false
                    }, {
                        name: '超值小样',
                        path: '/',
                        hot: false
                    }, {
                        name: '明星推荐',
                        path: '/',
                        hot: false
                    }, {
                        name: '最新活动',
                        path: '/',
                        hot: false
                    }, {
                        name: '新品上架',
                        path: '/',
                        hot: false
                    }, {
                        name: '本周特价',
                        path: '/',
                        hot: true
                    }, {
                        name: '清仓',
                        path: '/',
                        hot: true
                    }, {
                        name: '品牌库',
                        path: '/',
                        hot: false
                    },
                ]
            },
            selectHeadMenu(data) {
                this.headMenuText = data.name;
            },
            handleScroll () {  
                this.$nextTick(() => {
                    let scrollTop = document.documentElement.scrollTop || document.body.scrollTop;  
                    // let headerTop = document.getElementById("headerNav").offsetTop;
                    if (scrollTop  > 700) { 
                        this.isFixed = true;  
                    } else {  
                        this.isFixed = false;  
                    }  
                })	
            }
        },
        created() {
            this.init();
        },
        mounted() {
            window.addEventListener('scroll', this.handleScroll);
        },
        destroyed() {
            window.removeEventListener('scroll', this.handleScroll);
        }
    }
</script>

<style lang="scss" scoped>
    .header-info {
        height: 32px;
        background: #f8f8f8;
        line-height: 32px;
        border-bottom: solid 1px #e2e2e2;
        box-shadow: 0 1px 2px #e2e2e2;
        font-size: .75rem;
        color: #666666;
        .content {
            user-select: none;
            display: flex;
            justify-content: space-between;
            width: 1200px;
            min-width: 990px;
            margin: 0 auto;
            .left {
                span {
                    cursor: pointer;
                    &:hover {
                        color: #ff1a3a;
                        text-decoration: underline;
                    }
                }
            }
            .right {
                display: flex;
                color: #dddddd;
                &>div {
                    padding: 0 17px;
                    color: #666;
                }
                .menu-box {
                    position: relative;
                    .text {
                        span {
                            display: inline-block;
                            width: 7px;
                            height: 4px;
                            background: url('../assets/image/detail.gif') no-repeat -252px -30px;
                        }
                    }
                    .menu {
                        position: absolute;
                        padding: 5px 17px;
                        z-index: 10000;
                        white-space: nowrap;
                        top: 0;
                        left: 0;
                        line-height: 1;
                        background: #fefefe;
                        border: solid 1px #e2e2e2;
                        li {
                            padding: 5px 0;
                            cursor: pointer;
                            &:hover {
                                color: #ff1a3a;
                                text-decoration: underline;
                            }
                        }
                    }
                }
                .phone {
                    color: #ff1a3a;
                    font-size: 1.2rem;
                    font-family: Arial, Helvetica, sans-serif;
                    font-style: italic;
                    span {
                        display: inline-block;
                        width: 16px;
                        height: 13px;
                        background: url('../assets/image/detail.gif') no-repeat -269px -30px;
                        overflow: hidden;
                    }
                }
                .link {
                    cursor: pointer;
                }
            }
        }
    }

    .header-box {
        .content {
            display: flex;
            width: 1200px;
            min-width: 990px;
            margin: 0 auto;
            .logo {
                display: flex;
                justify-content: center;
                align-items: center;
                width: 184px;
                height: 92px;
                img {
                    width: 90%;
                }
            }
            .query-box {
                padding: 20px 0 12px 120px;
                .query-input {
                    display: flex;
                    input {
                        border: solid 2px #02a3f0;
                        padding: 8px;
                        width: 360px;
                        margin: 0;
                        color: #666666;
                        outline: none;
                    }
                    button {
                        background: #02a3f0;
                        padding: 8px 12px;
                        color: #fff;
                        border: solid 1px #02a3f0;
                    }
                }
                .hot {
                    padding-top: 5px;
                    color: #666;
                    span {
                        padding: 0 5px;
                        &.more-hot {
                            color: #ff1a3a;
                        }
                    }
                }
            }
            .qrcode-box {
                position: relative;
                width: 80px;
                height: 80px;
                background: url('../assets/image/qrcode-app.png') no-repeat;
                margin: 10px 72px;
                .moblie-menu {
                    position: absolute;
                    left: -50px;
                    border: 1px solid #999;
                    background: #fff;
                    width: 180px;
                    padding: 5px;
                    box-shadow: 3px 3px 5px #b8b8b8;
                    z-index: 9999;
                    .mobile-item {
                        display: flex;
                        border-bottom: 1px solid #ccc;
                        h5 {
                            line-height: 2;
                            color: #333;
                        }
                        .android,
                        .ios {
                            display: inline-block;
                            width: 25px;
                            height: 25px;
                            margin: 5px 5px 0 0;
                            background-image: url('../assets/image/mobile-system.png');
                        }
                        .ios {
                            background-position:  0 -26px;
                        }
                        &:last-of-type {
                            border: none;
                        }
                    }
                }
            }
            .shop-car {
                position: relative;
                margin: 20px 5px;
                .car-info {
                    position: relative;
                    line-height: 43px;
                    width: 195px;
                    padding-left: 70px;
                    height: 43px;
                    background: url('../assets/image/detail.gif') no-repeat;
                    background-position:  0 -30px;
                    z-index: 10000;
                    color: #666;
                    span {
                        color: #ff1a3a;
                        font-weight: 700;
                    }
                }
                &:hover .car-info {
                    background-position: 0 -74px;
                }

                .car-detail {
                    position: absolute;
                    z-index: 9999;
                    width: 290px;
                    bottom: -28px;
                    padding: 10px;
                    right: 1px;
                    background: #fff;
                    border: solid 1px #dcdcdc;
                    .empty {
                        line-height: 2;
                        color: #666;
                    }
                }
            }
        }
    }

    .header-nav {
        width: 100%;
        background: url('../assets/image/navbg.jpg') repeat-x;
        height: 40px;
        line-height: 40px;
        color: #fff;
        font-size: 1rem;
        min-width: 1200px;
        .content {
            display: flex;
            width: 1200px;
            margin: 0 auto;
            .menu {
                background: url('../assets/image/detail.gif') no-repeat 0 -117px;
                // padding: 0 65px;
                width: 230px;
                text-align: center;
                white-space: nowrap;
            }
            .nav {
                display: flex;
                .nav-item {
                    position: relative;
                    width: 122px;
                    white-space: nowrap;
                    text-align: center;
                    cursor: pointer;
                    span {
                        position: absolute;
                        right: 0;
                        color: #565656;
                    }
                    &:hover {
                        color: #2ad0ff;
                    }
                    &.hot {
                        color: #ff1a3a;
                    }
                }
            }
        }

        &.top {
            position: fixed;
            top: 0;
            z-index: 9999;
        }
    }
 
</style>
