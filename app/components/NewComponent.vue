<template>
  <Image ref="player" v-on="listeners" v-bind="attrs" />
</template>
<script>
// This wraps the nativescript-videoplayer in a component that auto destroys, so you don't have to
// https://github.com/nstudio/nativescript-videoplayer
// using techniques described in https://zendev.com/2018/05/31/transparent-wrapper-components-in-vue.html
export default {
  computed: {
    listeners() {
      const { ...listeners } = this.$listeners;
      return listeners;
    },
    attrs() {
      const { ...attrs } = this.$attrs;
      return attrs;
    }
  },
  beforeDestroy() {
    this.$refs.player.nativeView.destroy();
  }
};
</script>