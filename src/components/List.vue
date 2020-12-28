<template>
  <section>
    <ul>
      <Item
        v-for="task of tasks"
        :key="task.id"
        v-bind:task="task"
        v-on:task-checked="$emit('task-checked', task.id)"
      />
      <li v-if="!tasks.length">No tasks</li>
    </ul>
    <label>
      <input id="new-task" type="text" placeholder="Add new task" />
      <button v-on:click="$emit('task-added')">Add</button>
    </label>
  </section>
</template>

<script lang="ts">
import Item from "@/components/Item.vue";

export default {
  props: {
    tasks: {
      type: Array,
      required: true
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
