<template>
  <div class="mark" v-if="flag">对不起，此应用只能在移动端打开!</div>
</template>
<script>
export default {
  data() {
    return {
      flag: true
    };
  },
  mounted() {
    const _this = this;
    this.$nextTick(() => {
      _this.mark();
      window.onresize = function() {
        _this.mark();
      };
    });
  },
  methods: {
    mark() {
      let wid = window.screen.availWidth;
      let hei = window.screen.availHeight;
      if (wid >= 1024 || hei >= 1024) {
        this.flag = true;
        this.$store.state.state = false;
      } else {
        this.flag = false;
        this.$store.state.state = true;
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.mark {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 4;
  background: rgb(224, 216, 231);
  font-size: 40px;
}
</style>