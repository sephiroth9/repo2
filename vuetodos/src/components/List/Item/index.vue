<template>
  <div>
    <li  ref="li" @mouseenter="moveHandle()" @mouseleave="leaveHandle()">
      <input type="checkbox" />
      <span></span>
      <button ref="button" style="display: none">删除</button>
    </li>
  </div>
</template>
<script>

export default {
  props: ["todos"],
  methods: {
    moveHandle() {
      this.$refs.li.style.backgroundColor = "#ccc";
    },
    leaveHandle() {
      this.$refs.li.style.backgroundColor = "white";
    }
  },
};
</script>
<style lang="">
</style>