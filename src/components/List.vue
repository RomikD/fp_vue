<template>
  <section>
    <ul>
      <Item v-for="task of tasks" :key="task.id" v-bind:task="task" />
      <li v-if="!tasks.length">No tasks</li>
    </ul>
    <label>
      <input id="new-task" type="text" placeholder="Add new task" />
      <button v-on:click="add(tasks)">Add</button>
    </label>
  </section>
</template>

<script lang="ts">
import Item from "@/components/Item";

export default {
  props: {
    tasks: {
      type: [],
      required: true
    }
  },
  methods: {
    add(tasks: { id: number; title: string; completed: boolean }[]) {
      const input: HTMLInputElement | null = document.querySelector(
        "#new-task"
      );

      if (input?.value) {
        tasks.push({
          id: tasks.length,
          title: input.value,
          completed: false
        });
        input.value = "";
      }
    }
  },
  components: {
    Item
  }
};
</script>

<style scoped lang="scss">
ul {
  margin: 0;
  padding: 0;
}
input {
  border: 1px solid;
}
button {
  cursor: pointer;
}
</style>
