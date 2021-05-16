<template>
  <div class="root">
    <Title title="新闻动态"/>
    <News :newsList="newsList"/>
  </div>
</template>

<script>
  import Title from '@/pages/common/title';
  import News from '@/pages/home/news';

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }
  export default {
    components: {Title, News},
    data() {
      return {
        newsList: [
          {content: '贵阳报废汽车联系电话分析汽车报废公司盈利点'},
          {content: '贵阳高速困境救援拖车价格'},
          {content: '贵阳上门收购报废车分析报废车标准'},
          {content: '贵阳事故车回收厂家讲述自己洗车事项'},
          {content: '贵阳报废车收购讲述家用轿车报废年限  '},
          {content: '贵阳水淹车回收厂家讲述水淹车如何看  '},
          {content: '贵阳报废车收购价格哪里好  '},
          {content: '贵阳僵尸车回收 ​机动车报废程序  '},
          {content: '贵阳汽车报废不办手续会不会影响新车登记  '},
          {content: '贵阳上门收购报废车分析报废车不注销后果  '},
          {content: '贵阳事故车回收厂家讲述有效排除事故车方法  '},
          {content: '贵阳高价回收报废车热线  '},
          {content: '贵阳黄标车由于单车排放高，应优先管控和淘汰  '},
        ]
      }
    },
    mounted() {
      if (process.browser) {  // 在页面mounted生命周期里面 根据环境实例化WOW
        new WOW({}).init()
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '@/assets/styles/variables.scss';

  .card {
    border: 5px solid #e8e8e8;
    box-shadow: 3px 3px 12px #e8e8e8;
  }

  .card:hover {
    .picture {
      transform: translate(0, 0)
    }
  }

  .picture {
    object-fit: cover;
    transition: all 0.6s;
    transform: translate(-30px, -30px);

    &.special {
      transform: translate(30px, -30px)
    }
  }

  @media screen and (max-width: 992px) {
    .picture {
      transform: translate(0, 0) !important;
    }
    .card {
      border: none;
    }
    .top, .bottom {
      display: none;
    }
  }

  @media screen and (max-width: 768px) {
    .picture {
      height: 200px;
    }
  }

  .content {
    position: relative;

    .top {
      position: absolute;
      top: -5px;
      left: -5px;
      width: 0;
      height: 0;
      border-left: 5px solid $theme-color;
      border-top: 5px solid $theme-color;
      transition: all 0.6s;
    }

    .bottom {
      position: absolute;
      right: -5px;
      bottom: -5px;
      width: 0;
      height: 0;
      border-bottom: 5px solid $theme-color;
      border-right: 5px solid $theme-color;
      transition: all 0.6s;
    }
  }

  .content:hover {
    box-shadow: 3px 3px 12px $theme-color;

    .top, .bottom {
      width: 100%;
      height: 100%;
    }
  }
</style>
