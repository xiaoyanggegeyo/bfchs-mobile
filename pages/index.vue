<template>
  <div>
    <!--    顶部四个菜单-->
    <Menu style="margin-top: .8rem"/>
    <!--    关于我们-->
    <Title style="margin-top: .8rem" title="关于我们">
      <span slot="title-nav">  </span>
    </Title>
    <AboutUs style="margin-top: .8rem"/>
    <!--    汽车交易-->
    <Title style="margin-top: .8rem" title="汽车交易">
      <span slot="title-nav" @click="$router.push({path:'/product'})"> > </span>
    </Title>
    <Example :exampleList="exampleList"/>
    <div style="width: 100%;height: 10rem">
      <img src='~/static/img/home/1.jpg' alt="" style="display: inline-block; width: 100%;height: 100%">
    </div>

    <!--    新闻动态-->
    <Title style="margin-top: .8rem" title="新闻动态">
      <span slot="title-nav" @click="$router.push({path:'/business'})"> > </span>
    </Title>
    <News :newsList="newsList"/>

    <!--    <Product/>-->
    <!--    <Business/>-->
    <!--    <About/>-->
    <!--    <Partner/>-->
    <!--    <Client/>-->
    <!--    版权组件-->
    <Copyright style="margin-bottom: 4rem"/>
    <!--    底部导航栏-->
    <FooterNav/>
  </div>
</template>

<script>
  import Menu from '@/pages/home/menu';
  import AboutUs from '@/pages/common/about-us';
  import Title from '@/pages/common/title';
  import Example from '@/pages/home/example';
  import News from '@/pages/home/news';
  import Copyright from '@/pages/common/copyright';

  // import Product from '@/components/index/product'
  // import Business from '@/components/index/business'
  // import About from '@/components/index/about'
  // import Partner from '@/components/index/partner'
  // import Client from '@/components/index/client'
  import FooterNav from '@/pages/common/footer-nav';

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }

  export default {
    components: {
      Menu,
      Title,
      AboutUs,
      Example,
      News,
      FooterNav,
      Copyright


      // Product,
      // Business,
      // About,
      // Client,
      // Partner,
      // FooterNav
    },
    data() {
      return {
        exampleList: [
          {
            icon: require('~/static/img/example/1.jpg')
          }, {
            icon: require('~/static/img/example/2.jpg')
          }, {
            icon: require('~/static/img/example/3.jpg')
          }, {
            icon: require('~/static/img/example/4.jpg')
          }
        ],
        newsList: [
          {content: '贵阳报废汽车联系电话分析汽车报废公司盈利点'},
          {content: '贵阳高速困境救援拖车价格'},
          {content: '贵阳上门收购报废车分析报废车标准'}]
      }
    },
    mounted() {
      if (process.browser) {  // 在页面mounted生命周期里面 根据环境实例化WOW
        new WOW({}).init()
      }
      ;
      this.getExampleList();
      this.getNewsList();
    },
    methods: {
      getExampleList() {
        this.$axios.post('/commom/getGoodsList?pageNo=1&pageSize=4  &classId=1').then(res => {
          this.exampleList = res.data.data.items;
        })
      },
      getNewsList() {
        this.$axios.post('/commom/getInformationList?pageNo=1&pageSize=4').then(res => {
          this.newsList = res.data.data.items;
        })
      }
    }

  }
</script>

<style lang="scss" scoped>

</style>
