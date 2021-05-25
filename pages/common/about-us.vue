<template>
  <div class="root">
    <div class="top-box">
      <div class="left-box">
        <img class="img" :src=imgList[0].icon alt="">
      </div>
      <div class="right-box">
        贵阳专业收报废车中心：收报废车电话：15628008678刘先生
        是交管局指定的报废车专业解体厂！专业从事老旧机动车，事故车的报废解体业务。
      </div>
    </div>
    <div class="bottom-box">
      本中心实力雄厚拆解设备齐全，具有大批量拆解车辆的能力，且价格合理，因此与多家单位和个人建立了良好的业务关系，我们真诚地恭候广大企业和个人前来咨询洽谈。
    </div>
  </div>
</template>

<script>
  export default {
    name: "about-us",
    data() {
      return {
        imgList: [
          {icon: require('~/static/img/about/two.jpg')}]
      }
    },
  }
</script>

<style scoped lang="scss">
  .root {
    width: 100%;
    padding: .4rem;


    .top-box {

      display: flex;


      .left-box {

        flex: 1;
        width: 184px;
        height: 132px;

        .img {
          padding-top: 5px;
          width: 100%;
          height: 100%;
        }

      }

      .right-box {
        flex: 1;
        color: #666666;
        font-family: 微软雅黑;
        font-size: 1rem;
        line-height: 1.7rem;
        padding-left: 6px;

      }

    }

    .bottom-box {

      width: 100%;
      color: #666666;
      font-family: 微软雅黑;
      /*text-align: justify;*/
      font-size: 1rem;
      line-height: 1.7rem;
    }
  }

</style>
