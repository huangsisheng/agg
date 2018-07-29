<template>
<div class="agg_wrap" :data-id="i" @click="toggle">
  <!-- <div class="hammer" :data-index="i" >
    <img class="hammer_item" src="../images/hammer.png" alt="">
  </div> -->
  <div v-if="flag1" class="agg">
    <img class="agg_item" src="../images/agg.png" alt="">
  </div>
  <div class="agg-puo" v-if="flag2">
    <img class="agg-puo-item" src="../images/agg-puo.png" alt="">
  </div>
</div>
</template>
<script>
export default {
  props:["i"],
  data () {
    return {
      flag1:true,
      flag2:false,
      flag3:false,
      timer:0
    };
  },
  methods:{
    toggle(){
      this.flag1 = false;
      this.flag2 = true;
      this.flag3 = true;
      this.timer = setTimeout(() => {
        this.flag3 = false;
      }, 200);
    }
  },
}
</script>
<style lang="scss">
  @import "@/style/reset.scss";
  @import "@/style/common.scss";
  .agg_wrap{
    position: relative;
    .agg{
      position: absolute;
      .agg_item{
        width: 100%;
        height: 100%;
      }
    }
    .agg-puo{
      position: absolute;
        .agg-puo-item{
          width: 100%;
          height: 100%;
        }
    }
    .hammer{
      position: relative;
      width: px-rem(100);
      height: px-rem(100);
      .hammer_item{
        width: 100%;
        height: 100%;
        position: absolute;
        top: -2rem;
        left: -2rem;
      }
    }
  }
</style>