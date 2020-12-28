<template>
  <section>
    <ul>
      <Item v-for="task of tasks" :key="task.id" v-bind:task="task" />
    </ul>
  </section>
</template>
<script lang="ts">
import Item from "@/components/Item";

export default {
  props: ["tasks"],
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
</style>
