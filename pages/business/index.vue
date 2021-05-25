<template>
  <div class="root">
    <Title title="新闻动态"/>
    <News :newsList="newsList"/>
    <!--    版权组件-->
    <Copyright/>
  </div>
</template>

<script>
  import Title from '@/pages/common/title';
  import News from '@/pages/home/news';
  import Copyright from '@/pages/common/copyright';

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }
  export default {
    components: {Title, News, Copyright},
    data() {
      return {
        newsList: []
      }
    },
    mounted() {
      if (process.browser) {  // 在页面mounted生命周期里面 根据环境实例化WOW
        new WOW({}).init()
      }
      this.getNewsList();
    },
    methods: {
      getNewsList() {
        this.$axios.post('/commom/getInformationList?pageNo=1&pageSize=4').then(res => {
          this.newsList = res.data.data.items;
        })
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
