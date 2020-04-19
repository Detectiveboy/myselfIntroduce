<template>
  <div id="app">
    <Mark />
    <div class="time" v-if="flag" v-show="state">{{time}}</div>
    <stepOne v-show="state"></stepOne>
    <stepTwo v-show="state"></stepTwo>
    <div id="view">
      <router-view />
    </div>
    <div id="nav">
      <router-link to="/">首页</router-link>
      <router-link to="/about">关于</router-link>
      <router-link to="/my">作品</router-link>
      <router-link to="/contact">联系</router-link>
    </div>
  </div>
</template>
<script>
import stepOne from "@/components/Stepone.vue";
import stepTwo from "@/components/Steptwo.vue";
import Mark from "@/components/Mark.vue";
export default {
  data() {
    return {
      time: 5,
      flag: true,
      state: this.$store.state.state
    };
  },
  components: {
    stepOne,
    stepTwo,
    Mark
  },
  mounted() {
    this.$nextTick(() => {
      const timer = setInterval(() => {
        this.time--;
      }, 1000);
      setTimeout(() => {
        clearInterval(timer);
        this.flag = false;
      }, 6000);
    });
  }
};
</script>
<style lang="scss" scoped>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  position: relative;
  .time {
    width: 30px;
    height: 30px;
    border: 1px solid rgb(233, 31, 216);
    border-radius: 50%;
    font-size: 25px;
    text-align: center;
    line-height: 30px;
    color: rgb(233, 31, 216);
    position: absolute;
    top: 10px;
    right: 10px;
    z-index: 3;
  }
  #view {
    flex: 1;
    width: 100%;
    overflow: hidden;
    background: url("./assets/backgroundMain.jpg") no-repeat;
    background-size: 100% 100%;
  }
  #nav {
    width: 100%;
    height: 50px;
    background: rgb(211, 211, 228);
    display: flex;
    a {
      flex: 1;
      height: 100%;
      text-align: center;
      line-height: 50px;
    }
    .router-link-exact-active {
      background: rgb(177, 159, 192);
      color: rgb(233, 71, 211);
      font-size: 20px;
      font-weight: blod;
    }
  }
}
</style>
