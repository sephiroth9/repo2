<template lang="">
    <div id="header">
        <input type="text" @keyup.enter ="search">
    </div>
</template>
<script>
export default {
  methods: {
    search(event) {
        
        this.$emit('addToDos',event.currentTarget.value)
        event.currentTarget.value=""
    },
  },
};
</script>
<style scoped>
#header {
  text-align: center;
}
</style>