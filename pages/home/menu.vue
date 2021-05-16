<template>
  <div class="box">
    <div class="out-box">
      <div class="left-box" @click="$router.push({path:'/'})">首页</div>
      <div class="right-box" @click="$router.push({path:'/product'})">案例展示</div>
    </div>
    <div class="out-box">
      <div class="left-box" @click="$router.push({path:'/about'})">关于我们</div>
      <div class="right-box" @click="$router.push({path:'/technology'})">联系我们</div>
    </div>


  </div>

</template>

<script>
  export default {
    name: "menu"
  }
</script>

<style scoped lang="scss">
  .box {
    width: 100%;
    display: flex;
    flex-direction: column;


    .out-box {
      flex: 1;
      display: flex;
      padding-right: 2rem;
      padding-left: 2rem;
      padding-top: 1rem;


      .left-box {
        flex: 1;
        height: 42px;
        color: #333;
        font-size: 14px;
        text-align: center;
        line-height: 42px;
        border: 1px solid #ccc;
        border-radius: .4rem;
        margin-right: .7rem;

      }

      .right-box {
        flex: 1;
        height: 42px;
        color: #333;
        font-size: 14px;
        text-align: center;
        line-height: 42px;
        border: 1px solid #ccc;
        border-radius: .4rem;
        margin-left: .7rem;
      }
    }
  }

</style>
