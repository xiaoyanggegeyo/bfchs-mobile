<template>
  <div class="goodDetail">
    <div class="top-box">
      <!-- 主图 -->
      <div class="left-box">
        <img class="img" :src="detailsData.picUrl">
      </div>
      <!-- 富文本 -->
      <div class="right-box">
        <div class="name">{{detailsData.name}}</div>

      </div>
    </div>
    <div v-html="detailsData.detail" class="detail"></div>
    <!-- 图片列表 -->
    <!--    v-if="imgList.length != 0"-->
    <div class="bottomBox">

      <div class=" imgBox" v-for="(item,index) in imgList" :key="index">
        <img :src="item" alt="">
      </div>

    </div>
  </div>

</template>
<script>
  export default {
    name: "example-details",
    components: {},
    data() {
      return {
        //图片列表
        imgList: []

      }
    },
    props: {
      detailsData: {
        type: Object,
        default() {
          return {}
        }

      }
    },
    mounted() {
      //遍历detailUrl数组 有逗号才分割
      // if (this.detailsData.detailUrl && this.detailsData.detailUrl != null) {
      if (this.detailsData.detailUrl.indexOf(",") != -1) {
        this.imgList = this.detailsData.detailUrl.split(",");
      } else {
        this.imgList.push(this.detailsData.detailUrl);
      }
      // }
    }
  }
</script>
<style scoped lang="scss">
  .goodDetail {
    width: 100%;
    overflow-x: hidden;
    padding: 2rem;

    .top-box {
      display: flex;

      .left-box {
        width: 50%;

        .img {
          display: inline-block;
          width: 100%;
        }
      }

      .right-box {
        padding: 0 .5rem;
        width: 50%;

        .name {
          width: 80%;
          height: 25px;
          font-size: 12px;
          font-family: PingFang-SC-Medium, PingFang-SC;
          font-weight: 500;
          color: #444444;
          line-height: 25px;
          border-bottom: 1px solid #ccc;
          padding-bottom: 40px;
        }
      }
    }

    .detail {
      margin-top: .9rem;
      width: 100%;
      height: 100%;
      overflow: hidden;
    }
  }


  .bottomBox {
    width: 100%;
    overflow-x: scroll;
    .imgBox {
      display: inline-block;
      width: 30%;
      height: 100%;
      padding: 0 .5rem;
    }

    .imgBox img {
      display: inline-block;
      width: 100%;
      height: 100%;
    }
  }

</style>
