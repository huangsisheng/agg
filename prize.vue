<template>
  <transition enter-active-class="animated fadeIn" leave-active-class="animated fadeOut">
    <div class="luck" v-if="showToast">
      <div class="luck_wrap">
        <div class="sorry_wrap">
          <div class="sorry_wrap_item">
            <img class="sorry_pic" src="../assets/images/sorry.png" alt="">
          </div>
          <button class="agine" @click="close();send1();send2()">再来一次</button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    data() {
      return {
        showToast:true,
        continued:false,
      }
    },
    methods: {
      close() {
        this.showToast = false;
        this.continued = true;
        this.$emit("show",this.continued);
      },
      send1(){
        this.close();
        this.$bus.emit("show2", this.showToast);
      },
      send2() {
        this.close();
        this.$bus.emit("show3", this.continued);
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "@/style/reset.scss";
  @import "@/style/common.scss";
  .luck {
    position: absolute;
    top:0;
    left:0;
    z-index: 100;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    .luck_wrap {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 80%;
      text-align: center;
      .sorry_wrap {
        width: 90%;
        height: 70%;
        margin: 0 auto;
        margin-top: 0.5rem;
        .sorry_wrap_item {
          width: 100%;
          height: 85%;
          margin: 0 auto;
          margin-bottom: px-rem(25);
          .sorry_pic{
            width: 100%;
            height: 100%;
          }
        }
        .agine {
          border: none;
          outline: none;
          width: 80%;
          height: 1.5rem;
          border-radius: 1rem;
          background: red;
          background: red;
          font-weight: 600;
          color: #fff;
          font-size: px-rem(16);
        }
      }
      
    }
  }
</style>