<template>
  <div>
    <input
      type="checkbox"
      name=""
      id=""
      @click="inputHandle"
      :checked="this.count === todos.length && this.count != 0 ? true : false"
    />
    <label>
      <span> 已选择{{ count }} </span>
      <span> 全部{{ todos.length }}</span>
    </label>
  </div>
</template>
<script>
export default {
  props: ["todos"],
  methods: {
    inputHandle(event) {
      this.$emit("allCheckHandle", event.target.checked);
    },
  },

  computed: {
    count: function () {
      return this.todos.reduce((pre, current) => {
        return pre + (current.done ? 1 : 0);
      }, 0);
    },
  },
};
</script>
<style lang="">
</style>