<template>
<div class="egg_container">
  <div class="stage">
    <div class="egg_box" :class="{paused:flag,continue1:continued}">
      <div class="egg" :class="{paused2:flag,continue2:continued}" v-for="i in 3" :key="i" @click="click">
         <Open :i="i" :pre1="pre1"></Open>
      </div>
    </div>
  </div>
  <!-- 弹窗 -->
  <Prize :continued="continued" v-if="flag2" @show="show"></Prize>
</div>
</template>
<script>
  import Open from "./open";
  import Prize from "./prize";
export default {
  components:{Open, Prize},
  data () {
    return {
      flag:false,
      flag2:false,
      continued:false,
      pre1: false,
      tickts:3,
      activeIndex:-1
    };
  },
  beforeupdated() {
    this.click()
  },
  methods:{
    click(index){
      if(this.tickts<=0){
        this.tickts = 0;
        this.pre1 = false;
        alert("您的抽奖次数已用完");
      }else{
        this.tickts--;
        this.flag = true;
        setTimeout(() => {
          this.flag2 = !this.flag2;
          console.log(this.flag2);
        }, 200);
      }
    },
    show(continued){
      this.continued = continued;
    }
  },
}
</script>
<style lang="scss">
  @import "@/style/reset.scss";
  @import "@/style/common.scss";
  .egg_container{
    overflow: hidden;
    width: 100%;
    height: 100%;
    background: url("../assets/images/bg.jpg") no-repeat center center;
    .stage{
      position: relative;
      display: flex;
      justify-content: center;
      overflow: hidden;
      width: 100%;
      height: 75%;
      background: url("../assets/images/stage.png") no-repeat;
      background-size:cover;
      .egg_box{
        position: absolute;
        bottom: 4rem;
        width: px-rem(200);
        height: px-rem(180);
        border-radius: 50%;
        animation: a 1000s linear;
        .egg{
          width: px-rem(100);
          height: px-rem(100);
          float: left;
          overflow: hidden;
        }
        .paused2{
          animation-play-state: paused;
        }
        .continue2{
          animation: b 1000s linear,zindex 10000ms 0ms infinite linear;
        }
      }
      .paused{
        animation-play-state: paused;
      }
      .continue1{
        animation: a 1000s linear;
      }
    }
  }
.egg:nth-child(1){
    margin-top: 45%;
    /* animation: b 1000s linear; */
    animation: b 1000s linear,zindex 10000ms 0ms infinite linear;
}
.egg:nth-child(2){
    margin-top: -5%;
    margin-left: -5%;
    /* animation: b 1000s linear; */
    animation: b 1000s linear,zindex 10000ms -2500ms infinite linear;
}
.egg:nth-child(3){
    margin-top: -5%;
    margin-right: -5%;
    /* animation: b 1000s linear; */
    animation: b 1000s linear,zindex 10000ms -5500ms infinite linear;
}

@keyframes a{
  0% {
      transform: rotate(0deg);
  }
  to{
      transform: rotate(36000deg);
  }
}
@keyframes b{
  0% {
      transform: rotate(0deg);
  }
  to{
      transform: rotate(-36000deg);
  }
}
</style>