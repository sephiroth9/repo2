

<template>
  <div id="wrap">
    <Header @addToDos="addToDos" />
    <List :todos="toDos" @inputChange="inputChange" @delHandle="delHandle"/>
    <Footer :todos ="toDos" @allCheckHandle="allCheckHandle"/>
  </div>
</template>

<script>
import Header from "./components/Header";
import List from "./components/List";
import Footer from "./components/Footer";
import { nanoid } from "nanoid";

export default {
  data() {
    return {
      toDos: [
        { id: "001", name: "吃饭", done: true },
        { id: "002", name: "睡觉", done: true },
        { id: "003", name: "代码", done: false },
      ],
    };
  },

  methods: {

    addToDos(arg) {
      this.toDos = [{ id: nanoid(), name: arg, done: false }, ...this.toDos];
    },

    inputChange(id, checked) {
      
      this.toDos.map((todo) => {
        if (todo.id === id) {
          todo.done = checked;
        }
      })
    },

    delHandle(id){
      const newToDos = this.toDos.filter((todo)=>{
        return todo.id !== id
      })
    console.log(newToDos);
     this.toDos = newToDos
    },

    allCheckHandle(check){
      this.toDos.map((el)=>{
        el.done = check
      })
    }
    
  },
  name: "App",
  components: {
    Header,
    List,
    Footer,
  },
};
</script>

<style scoped>
#wrap {
  width: 500px;
  height: 200px;

  color: #2c3e50;
  margin: 0 auto;
}
</style>
