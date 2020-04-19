<template>
  <div class="stepTwo" v-if="flag[0]">
    <p>欢迎来到自我介绍</p>
  </div>
</template>
<script>
export default {
  name: "steptwo",
  data() {
    return {
      flag: [true]
    };
  },
  mounted() {
    this.$nextTick(() => {
      setTimeout(() => {
        this.$set(this.flag, 0, false);
      }, 6000);
    });
  }
};
</script>
<style lang="scss" scoped>
.stepTwo {
  width: 100%;
  height: 100%;
  position: relative;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  background: url("../assets/background03.jpg") no-repeat;
  background-size: 100% 100%;
  p {
    width: 240px;
    height: 30px;
    font-size: 30px;
    color: rgb(233, 31, 216);
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
  }
}
</style>