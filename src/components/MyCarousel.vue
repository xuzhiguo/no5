<template>
    <div class="carousel-box">
        <ul>
            <li v-for="(item,idx) in dataList" :key="idx" :class="{'active':idx == activeIdx}"
               :style="'background: url(' + item.url + ') ' + item.bgColor + ' center center no-repeat;'" >
            </li>
        </ul>
        <div class="indicator">
            <div class="btn">
                <span v-for="(item,idx) in dataList" :key="idx" :class="{'active': idx == activeIdx}"
                    @click="setSlideActive(idx)">{{idx+1}}</span>
            </div>
        </div>
    </div>
</template>

<script>
    let timer;

    export default {
        data () {
            return {
                activeIdx: 0
            }
        },
        components: {},
        props: {
            dataList: {
                type: Array,
                required: true
            },
            interval: {
                type: Number,
                default: 4000
            }
        },
        methods: {
            play() {
                // console.log(this.activeIdx, this.dataList.length);
                if(this.activeIdx >= this.dataList.length -1) {
                    this.activeIdx = 0;
                } else {
                    this.activeIdx++;
                }
            },
            setSlideActive(idx) {
                this.activeIdx = idx;
                this.init();
            },
            init() {
                timer && (clearInterval(timer));
                timer = setInterval(this.play, this.interval);
            }
        },
        mounted() {
            this.init();
        }
    }
</script>

<style lang="scss" scoped>
    .carousel-box {
        position: relative;
        height: 100%;
        width: 100%;
        ul {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 100%;
            li {
                position: absolute;
                transition: all .5s;
                height: 100%;
                width: 100%;
                top: 0;
                left: 0;
                opacity: 0;
                &.active {
                    opacity: 1;
                }
            }
        }
        .indicator {
            position: relative;
            height: 100%;
            width: 1200px;
            margin: 0 auto;
            // background: transparent;
            .btn {
                position: absolute;
                left: 240px;
                bottom: 10px;
                z-index: 999;
                span {
                    display: inline-block;
                    background: #fff;
                    color: #666;
                    height: 22px;
                    width: 22px;
                    line-height: 22px;
                    text-align: center;
                    margin-right: 10px;
                    border-radius: 50%;
                    cursor: pointer;
                    box-shadow: 0 0 3px #8e8888;
                    &.active {
                        background: #00b5ff;
                        color: #fff;
                    }
                }
            }
        }
    }
 
</style>
