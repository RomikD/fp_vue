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

<template>
  <div class="home">
    <!--    <img alt="Vue logo" src="../assets/logo.png" />-->
    <!--    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />-->

    <List
      v-bind:tasks="tasks"
      v-on:task-added="addTask"
      v-on:task-checked="checkTask"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue";
import List from "@/components/List.vue";

@Component({
  created() {
    const tasks: string | null = localStorage.getItem("tasks");

    if (tasks) {
      this.$data.tasks = JSON.parse(tasks);
    }
  },
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    addTask() {
      const input: HTMLInputElement | null = document.querySelector(
        "#new-task"
      );

      if (input?.value) {
        this.$data.tasks.push({
          id: this.$data.tasks.length,
          title: input.value,
          completed: false
        });
        input.value = "";

        localStorage.setItem("tasks", JSON.stringify(this.$data.tasks));
      }
    },
    checkTask(id: number) {
      this.$data.tasks[id].completed = !this.$data.tasks[id].completed;

      localStorage.setItem("tasks", JSON.stringify(this.$data.tasks));
    }
  },
  components: {
    HelloWorld,
    List
  }
})
export default class Home extends Vue {}
</script>
