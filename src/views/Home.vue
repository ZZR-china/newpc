<template>
  <div class="home">
    <!-- swiper -->
    <swiper :options="swiperOption" class="container">
      <swiper-slide class="part1" data-hash="slide1">
        <header class="header">
          <el-row :gutter="20" type="flex" class="row-bg" justify="space-between">
            <el-col :span="6" style="text-align:left;padding-left:0;margin-left: -2px;" :pull="0">
              <img src="../assets/images/pc_ico_logo.png" style="width: 90px;height: auto;" alt="logo">
            </el-col>
            <el-col :span="14" :push="0">
              <el-row :gutter="0" type="flex" justify="center" class="menu">
                <el-col :span="4" v-for="item in header" :key="item">
                  <span>{{item}}</span>
                </el-col>
              </el-row>
            </el-col>
          </el-row>
        </header>
        <swiper :options="part1swiperOption" class="part1-swiper">
          <swiper-slide>
            <img src="../assets/images/banner/ban_1.png" alt="banner1">
          </swiper-slide>
          <swiper-slide>
            <img src="../assets/images/banner/ban_2.png" alt="banner2">
          </swiper-slide>
          <swiper-slide>
            <img src="../assets/images/banner/ban_3.png" alt="banner3">
          </swiper-slide>
          <div class="swiper-pagination swiper-pagination-part1" slot="pagination"></div>
        </swiper>
        <div class="part1-footer">
          <el-row :gutter="0" type="flex" justify="center">
            <el-col :span="6" v-for="item in part1Footer" :key="item">
              <img :src="item.img" :alt="item.text">
              <div class="tips">{{item.text}}</div>
              <div class="hover-tips">
                <div class="title">
                  <span>{{item.hovertitle}}</span>
                </div>
                <div class="text" v-for="iitem in item.hovertext" :key="iitem">{{iitem}}</div>
              </div>
            </el-col>
          </el-row>
        </div>
      </swiper-slide>
      <swiper-slide class="part2" data-hash="slide2">
        <HomeHeader />
        <div class="part2-main">
          <el-row type="flex" justify="center" class="row-bg">
            <el-col :span="6"  
            v-for="item in part2List" 
            :key="item.text">
              <div class="elem" >
                <div class="elem-main" :style="{backgroundImage:'url(' + item.bgImg + ')'}">
                  <div class="elem-main-circle">
                    {{item.text}}
                  </div>
                  <div class="elem-main-block">
                    <div class="elem-main-block__circle part2__circle">
                      <img :src="item.topImg" :alt="item.text">
                    </div>
                    <MinLine :count="10"></MinLine>
                    <div class="elem-main-block__text">{{item.middletext}}</div>
                    <MinLine :count="10"></MinLine>
                    <div class="elem-main-block__circle part2__circle">
                      <img :src="item.footerImg" :alt="item.text">
                    </div>
                  </div>
                </div>
                <p class="elem-text">{{item.footertext}}</p>
              </div>
            </el-col>
          </el-row>
        </div>
      </swiper-slide>
      <swiper-slide class="part3" data-hash="slide3">
        <HomeHeader />
        <div>
          <img src="../assets/images/slide3.png" alt="slide3">
        </div>
      </swiper-slide>
      <swiper-slide class="part4" data-hash="slide4">
        <HomeHeader />
        <div class="main">
          <div class="title">合作品牌</div>
          <div class="tips">妙寄已和多家快递品牌建立合作关系</div>
          <el-row :gutter="0" justify="center" class="brand">
            <el-col class="brand-col" :span="6" v-for="item in part4List" :key="item.key">
              <div class="show">
                <img :src="item.show" alt="">
              </div>
              <div class="hover">
                <img :src="item.hover" alt="">
              </div>
            </el-col>
          </el-row>
        </div>
      </swiper-slide>
      <swiper-slide class="part5" data-hash="slide5">
        <HomeHeader />
        <div class="main">
          <div class="title">目前规模</div>
          <div class="tips">截至目前妙寄全国站点分布</div>
          <img src="../assets/images/hom_map.png" alt="part5home">
        </div>
      </swiper-slide>
      <swiper-slide class="part6" data-hash="slide6">
        <HomeHeader />
        <el-row>
          <el-col :span="12">
            <img src="../assets/images/hom_pho.png" alt="phone">
          </el-col>
          <el-col :span="10">
            <HomeForm></HomeForm>
          </el-col>
        </el-row>
      </swiper-slide>
      <div class="swiper-pagination swiper-pagination-container" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
// @ is an alias to /src
import HomeHeader from '@/components/HomeHeader.vue'
import HomeForm from '@/components/HomeForm.vue'
import MinLine from '@/components/MinLine.vue'

export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeForm,
    MinLine
  },
  data () {
    return {
      swiperOption: {
        direction: 'vertical',
        autoplay: false,
        hashNavigation: {
          watchState: true,
        },
        pagination: {
          el: '.swiper-pagination-container',
          clickable: true
        }
      },
      part1swiperOption: {
        effect: 'fade',
        loop: true,
        autoplay: true,
        preventClicks: false,
        preventLinksPropagation: false,
        pagination: {
          el: '.swiper-pagination-part1',
          clickable: true
        }
      },
      header: [
        '快递查询',
        '产品体系',
        '快递合作',
        '商务合作',
        '城市合伙人',
        '关于我们',
      ],
      part1Footer: [
        {
          img: require('../assets/images/gongx.png'),
          text: '共配体系',
          hovertitle: '软件+硬件',
          hovertext: [
            '软件：共配sys',
            '硬件：智能高端分拣设配',
          ],
        },
        {
          img: require('../assets/images/moduan.png'),
          text: '末端体系',
          hovertitle: '快递+新零售',
          hovertext: [
            '快递末端：门店+智能快递柜+派送',
            '智能下单：微信+支付宝+电话',
            '新零售：销售+体验+广告+冷链',
          ],
        },
        {
          img: require('../assets/images/fuw.png'),
          text: '服务体系',
          hovertitle: '服务+结算',
          hovertext: [
            '服务：智能客服',
            '结算：网点财务软件',
          ],
        },
        {
          img: require('../assets/images/dians.png'),
          text: '电商体系',
          hovertitle: '平台+商业+培训',
          hovertext: [
            '拼多多、京东',
            '商业：产品销售',
            '培训：电商培训',
          ],
        }
      ],
      part2List: [
        {
          bgImg: require('../assets/images/hom_con.png'),
          text: '连接',
          topImg: require('../assets/images/hom_pac.png'),
          footerImg: require('../assets/images/home_min.png'),
          middletext: '物与人得连接',
          footertext: '妙寄是一种连接节点'
        },
        {
          bgImg: require('../assets/images/hom_ser.png'),
          text: '服务',
          topImg: require('../assets/images/home_min.png'),
          footerImg: require('../assets/images/home_min.png'),
          middletext: '人与人得连接',
          footertext: '妙寄是一种底盘大网'
        },
        {
          bgImg: require('../assets/images/hom_lov.png'),
          text: '关怀',
          topImg: require('../assets/images/hom_hea.png'),
          footerImg: require('../assets/images/hom_hea.png'),
          middletext: '心与心的连接',
          footertext: '妙寄是一种连接节点'
        },
      ],
      part4List: [
        {
          show: require('../assets/images/zho2.png'),
          hover: require('../assets/images/zho.png'),
          key: 1,
        },
        {
          show: require('../assets/images/yun2.png'),
          hover: require('../assets/images/yun.png'),
          key: 1,
        },
        {
          show: require('../assets/images/yuan2.png'),
          hover: require('../assets/images/yuan.png'),
          key: 1,
        },
        {
          show: require('../assets/images/bai2.png'),
          hover: require('../assets/images/bai.png'),
          key: 1,
        },
        {
          show: require('../assets/images/shun2.png'),
          hover: require('../assets/images/shun.png'),
          key: 1,
        },
        {
          show: require('../assets/images/jing2.png'),
          hover: require('../assets/images/jing.png'),
          key: 1,
        },
        {
          show: require('../assets/images/sud2.png'),
          hover: require('../assets/images/sud.png'),
          key: 1,
        },
        {
          show: require('../assets/images/min2.png'),
          hover: require('../assets/images/min.png'),
          key: 1,
        },
        {
          show: require('../assets/images/ma2.png'),
          hover: require('../assets/images/ma.png'),
          key: 1,
        },
        {
          show: require('../assets/images/pin2.png'),
          hover: require('../assets/images/pin.png'),
          key: 1,
        },
        {
          show: require('../assets/images/de2.png'),
          hover: require('../assets/images/de.png'),
          key: 1,
        },
        {
          show: require('../assets/images/ke2.png'),
          hover: require('../assets/images/ke.png'),
          key: 1,
        },
        {
          show: require('../assets/images/bi2.png'),
          hover: require('../assets/images/bi.png'),
          key: 1,
        },
        {
          show: require('../assets/images/yi2.png'),
          hover: require('../assets/images/yi.png'),
          key: 1,
        },
        {
          show: require('../assets/images/fei2.png'),
          hover: require('../assets/images/fei.png'),
          key: 1,
        },
        {
          show: require('../assets/images/su2.png'),
          hover: require('../assets/images/su.png'),
          key: 1,
        },
      ]
    } 
  },
}
</script>

<style scoped lang="less">

.home {
  .container {
    width: 100%;
    height: 100vh;
    .part1 {
      header {
        position: absolute;
        top: 40px;
        left: 20%;
        z-index: 9999;
        width: 60%;
      }
      .menu {
        color: white;
        font-size: 12px;
        cursor: pointer;
        .el-col {
          padding-bottom: 10px;
          span {
            padding-bottom: 10px;
          }
          &:hover {
            span {
              border-bottom: 1px solid white; 
            }
          }
        }
      }
      .part1-swiper {
        width: 100%;
        height: 83vh;
        .swiper-slide {
          img {
            width: 100%;
            height: 100%;
          }
        }
        .swiper-pagination-part1 {
          bottom: 10vh;
        }
      }
      .part1-footer {
        position: absolute;
        bottom: 1%;
        left: 19%;
        width: 62%;
        background: white;
        box-shadow: 10px 2px 15px #f5f5f5;
        border-radius: 6px;
        z-index: 9999;
        .el-row {
          height: 24vh;
          .el-col {
            display: flex;
            padding: 10px 0px;
            justify-content:center;
            align-items:Center;
            flex-direction: column;
            font-size: 12px;
            &:hover {
              background: #f9f9f9;
              .tips {
                display: none;
              }
              .hover-tips {
                display: block;
              }
            }
            img {
              height: 50px;
            }
            .tips {
              font-size: 14px;
              padding-top: 26px;
            }
            .hover-tips {
              display: none;
              padding-top: 15px;
              .title {
                color: #e94c1d;
                margin-bottom: 15px;
                span {
                  padding-bottom: 5px;
                  border-bottom: 1px solid #e94c1d;
                }
              }
            }
          }
        }
      }
    }

    .part2 {
      .part2__circle {
        width: 70px;
        height: 70px;
        border-radius: 50%;
        background-color: rgba(245, 236, 236, 0.6);
        line-height: 70px;
        margin-left: 30%;
        display: flex;
        justify-content:center;
        align-items:Center;
        img {
          width: 40px;
        }
      }
      &-main {
        padding: 10vh 10vw 0 10vw;
        .elem {
          &-main {
            height: 400px;
            background: no-repeat;
            background-size: 100% 100%;
            display: flex;
            justify-content:center;
            align-items:Center;
            &:hover {
              .elem-main-circle {
                display: none;
              }
              .elem-main-block {
                display: block;
              }
            }
            &-circle {
              .part2__circle;
              margin-left: 0;
            }
            &-block {
              display: none;
              &__text {
                width: 160px;
                padding: 4px 10px;
                border-radius: 15px;
                font-size: 14px;
                background: rgba(245, 236, 236, 0.6);
              }
            }
          }
          &-text {
            font-size: 14px;
          }
        }
      }
    }

    .part3 {
      div {
        img {
          width: 100vw;
          height: 100vh;
          margin-top: -68px;
        }
      }
    }

    .part4 {
      .main {
        width: 100%;
        height: calc(~"100% - 68px");
        background: url('../assets/images/hom_par.png') no-repeat;
        background-size: 100% 100%;
        .brand {
          &-col {
            &:hover {
              .show {
                display: none;
              }
              .hover {
                display: block;
              }
            }
            .show {
              
            }
            .hover {
              display: none;
            }
          }
        }
      }
    }

    .part5 {
      .main {
        width: 100%;
        height: calc(~"100% - 68px");
        background: url('../assets/images/hom_pre.png') no-repeat;
        background-size: 100% 100%;
      }
    }
  }
}
</style>