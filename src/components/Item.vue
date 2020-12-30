<template>
  <li
    v-on:click="$emit('task-checked', task.id)"
    v-bind:class="{ checked: task.completed }"
  >
    {{ task.title }}
    <button class="rm" v-on:click="$emit('remove-todo', task.id)">
      &times;
    </button>
  </li>
</template>
<script lang="ts">
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  }
  // methods: {
  //   checkTask(task: { id: number; title: string; completed: boolean }) {
  //     task.completed = !task.completed;
  //   }
  // }
};
</script>
<style scoped lang="scss">
li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;

  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;

  &:nth-child(odd) {
    background: #f9f9f9;
  }

  &:hover {
    background: #ddd;
  }

  &.checked {
    background: #888;
    color: #fff;
    text-decoration: line-through;

    &::before {
      content: "";
      position: absolute;
      border-color: #fff;
      border-style: solid;
      border-width: 0 2px 2px 0;
      top: 10px;
      left: 16px;
      transform: rotate(45deg);
      height: 15px;
      width: 7px;
    }
  }
}
</style>
