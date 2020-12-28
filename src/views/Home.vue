<template>
  <div class="home">
    <!--    <img alt="Vue logo" src="../assets/logo.png" />-->
    <!--    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />-->

    <List v-bind:tasks="tasks" />
  </div>
</template>
<style lang="scss">
* {
  box-sizing: border-box;
}

.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;

  &:hover {
    background-color: #f44336;
    color: white;
  }
}
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;

  &:after {
    content: "";
    display: table;
    clear: both;
  }
}
input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 16px;
}
.addBtn {
  padding: 10px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;

  &:hover {
    background-color: #bbb;
  }
}
</style>
<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue";
import List from "@/components/List.vue";

@Component({
  data() {
    return {
      tasks: [
      ]
    };
  },
  components: {
    HelloWorld,
    List
  }
})
export default class Home extends Vue {}
</script>
