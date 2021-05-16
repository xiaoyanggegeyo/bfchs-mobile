<template>
  <div class="root">
    <div class="item" v-for="(item,index) in newsList" :key="index"
         :style="index == newsList.length - 1 ? '':'border-bottom:1px solid #ccc'">
      <span>{{item.content}}</span>
      <div class="time">{{dateFormat('YYYY/mm/dd',new Date())}}</div>
    </div>

  </div>
</template>

<script>

  export default {
    name: "news",
    data() {
      return {}
    },
    props: {
      newsList: {
        type: Array,
        default: function () {
          return [];
        }
      }
    },
    methods: {
      dateFormat(fmt, date) {
        let ret;
        const opt = {
          "Y+": date.getFullYear().toString(),        // 年
          "m+": (date.getMonth() + 1).toString(),     // 月
          "d+": date.getDate().toString(),            // 日
          "H+": date.getHours().toString(),           // 时
          "M+": date.getMinutes().toString(),         // 分
          "S+": date.getSeconds().toString()          // 秒
          // 有其他格式化字符需求可以继续添加，必须转化成字符串
        };
        for (let k in opt) {
          ret = new RegExp("(" + k + ")").exec(fmt);
          if (ret) {
            fmt = fmt.replace(ret[1], (ret[1].length == 1) ? (opt[k]) : (opt[k].padStart(ret[1].length, "0")))
          }
          ;
        }
        ;
        return fmt;
      }
    }
  }
</script>

<style scoped lang="scss">
  .root {
    width: 100%;
    padding: .8rem;

    .item {
      width: 100%;
      padding: .5rem 0;
      color: #222222;
      font-size: 16px;
      font-family: 微软雅黑;
    }

    .time {
      padding: 6px 0;
      color: #848E98;
      font-size: 12px;
    }
  }

</style>
