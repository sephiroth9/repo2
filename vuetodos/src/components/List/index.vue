<template>
  <div>
    <ul>
      <li
        v-for="item in todos"
        :key="item.id"
        @mouseenter="enterHandle"
        @mouseleave="leaveHandle"
        class=""
      >
        <input
          type="checkbox"
          :checked="item.done"
          @click="inputChange"
          :value="item.id"
        />
        <span>{{ item.name }}</span>
        <button class="display" @click="delHandle" :value="item.id">删除</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["todos"],
  data() {
    return {
        
      isActive: false,
      display: true,
    };
  },
  methods: {
    enterHandle(event) {
      
      event.target.setAttribute("class", "active");
      event.target.children[2].setAttribute("class", "");
    },
    leaveHandle(event) {
      event.target.setAttribute("class", "");
      event.target.children[2].setAttribute("class", "display");
    },
    inputChange(event) {
      this.$emit("inputChange", event.target.value, event.target.checked);
    },

    delHandle(event){
        
        this.$emit('delHandle',event.target.value)
    }
  },
  components: {},
};
</script>
<style scoped>
.active {
  background-color: #ccc;
}
.display {
  display: none;
}
</style>