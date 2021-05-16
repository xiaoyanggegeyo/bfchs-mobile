<template>
  <div class="root">
    <Title title="关于我们"/>
    <AboutUs/>
  </div>

</template>

<script>

  import {mapState, mapMutations} from 'vuex';
  import smoothscroll from 'smoothscroll-polyfill';
  import AboutUs from '@/pages/common/about-us';
  import Title from '@/pages/common/title';


  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
    smoothscroll.polyfill()
  }


  export default {
    components: {Title, AboutUs},
    data() {
      return {
        topList: [],
        navHeight: 0,
        navTop: 0,
        showNavFixed: false,
        active: 0,
        list: [
          {
            title: '公司介绍',
            desc: `江苏贵阳专业收报废车中心数据技术有限公司（简称贵阳专业收报废车中心）成立于2017年，是国家级高新技术软件企业，专业从事云计算、大数据和智慧城市等领域的产品研发及技术服务；贵阳专业收报废车中心秉持“以人为本、客户至上、生态协作、诚信敬业”的经营理念，从客户实际需求出发，为客户提供行业化的DT、IT设计咨询、方案规划、建设交付、运营维护、综合运营、行业应用软件开发等全方位的解决方案及技术服务。<br/>
          贵阳专业收报废车中心根植江苏、辐射全国，拥有一支扎实稳固的高端技术人才团队，成功建设了江苏省政府、江苏省公安厅、南京市政府、建邺区、溧水区等大数据平台，助力政务互联网化；为中天集团、悦达起亚等生产企业提供智慧城市信息化整体解决方案，助力产业互联网化。<br/>
          “精于开发，长于数据”贵阳专业收报废车中心作为大数据时代卓越的技术与服务提供商，我们将不断创新与实践，赋能更多的客户及生态伙伴。`
          },
          {
            title: '企业文化',
            desc: `愿景：成为您身边的大数据专家。<br/>
          使命：助力政府和企业的数字化转型。<br/>
          核心价值观：客户至上、生态协助、诚信敬业。`
          },
          {
            title: '荣誉资质',
            desc: `信用等级AAA认证<br/>
          ISO9001质量管理体系认证<br/>
          ISO27001信息安全管理体系认证<br/>
          双软企业认证<br/>
          高新企业`
          },
          // {
          //   title: '公司新闻',
          //   desc: `公司最新的动态，重大事件`
          // },
          {
            title: '联系我们'
          },
        ]
      }
    },
    watch: {
      subNavIndex(newVal, oldVal) {
        this.active = newVal - 1
        setTimeout(() => {
          this.handleNavClick(this.active)
        }, 0)
      },
      // active(newVal, oldVal) {
      //   setTimeout(() => {
      //     this.handleNavClick(newVal)
      //   }, 0)
      // }
    },
    computed: {
      ...mapState(['headerHeight', 'subNavIndex'])
    },
    mounted() {
      if (process.browser) {  // 在页面mounted生命周期里面 根据环境实例化WOW
        new WOW({}).init()
      }

      this.getTitleHeight()

      this.active = this.subNavIndex == 0 ? 0 : this.subNavIndex - 1
      if (this.active != 0) {
        setTimeout(() => {
          this.handleNavClick(this.active)
        }, 0)
      }

      window.addEventListener('scroll', this.handleWindowScroll)
      window.addEventListener('resize', this.handleWindowResize)
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleWindowScroll)
      window.removeEventListener('resize', this.handleWindowResize)
    },
    methods: {
      // 点击切换tab
      handleNavClick(index) {
        // this.active = index
        window.scrollTo({
          top: this.topList[index] - this.headerHeight - this.navHeight,
          left: 0,
          behavior: "smooth"
        })
        console.log(this.topList[index] - this.headerHeight - this.navHeight)
      },
      // 监听窗口滚动
      handleWindowScroll(e) {
        const myTop = document.documentElement.scrollTop || document.body.scrollTop
        // 固定tab
        const flag = myTop > this.navTop - this.headerHeight
        if (this.showNavFixed != flag) {
          this.showNavFixed = flag
        }
        // 高亮tab-item
        const list = [...this.topList, 9999]
        const doubleBarHeight = this.navHeight + this.headerHeight
        for (let i = 0, len = list.length; i < len; i++) {
          if (myTop >= list[i] - doubleBarHeight && myTop < list[i + 1] - doubleBarHeight) {
            this.active = i
          }
        }
      },
      // 获取每个title、nav的高度
      getTitleHeight() {
        // const titleList = this.$refs.title
        // this.topList = titleList.map(val => {
        //   return val.offsetTop
        // })
        // const navHeight = this.$refs.nav.clientHeight
        // this.navHeight = navHeight
        // const navTop = this.$refs.nav.offsetTop
        // this.navTop = navTop
      },
      // 改变窗口大小重新获取title、nav高度
      handleWindowResize() {
        this.$nextTick(() => {
          this.getTitleHeight()
        })
        this.handleNavClick(this.active)
      }
    }
  }
</script>

<style lang="scss" scoped>

  .root{
    margin-top: 2rem;
  }
  .navFixed {
    position: fixed;
    left: 0;
    right: 0;
    z-index: 9;
    background: #fff;
  }

  .bar {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 15px 0;
    border-bottom: 1px solid #dee2e6;
    font-size: 16px;
    color: #333;

    .bar-item {
      cursor: pointer;

      &.active {
        color: #007bff;
      }
    }
  }

  /deep/ .nav-tabs .nav-item .nav-link {
    border-color: transparent !important;
    font-size: 16px;
    color: #333;

    &.active {
      color: #007bff;
    }

    &:hover {
      color: #007bff;
    }
  }

  .desc {
    line-height: 3;
  }
</style>
