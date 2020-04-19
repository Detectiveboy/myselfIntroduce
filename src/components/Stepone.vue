<template>
  <div v-if="flag[0]" class="stepOne">
    <p>你好啊！</p>
  </div>
</template>
<script>
export default {
  name: "stepone",
  data() {
    return {
      flag: [true]
    };
  },
  mounted() {
    this.$nextTick(() => {
      setTimeout(() => {
        this.$set(this.flag, 0, false);
      }, 3000);
    });
  }
};
</script>
<style lang="scss" scoped>
.stepOne {
  width: 100%;
  height: 100%;
  background: url("../assets/background02.jpg") no-repeat;
  background-size: 100% 100%;
  position: relative;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  p {
    width: 120px;
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