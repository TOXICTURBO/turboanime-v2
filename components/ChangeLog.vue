<template>
  <div>
    <h1>Changelog</h1>
    <p>Here are the latest updates:</p>
    <ul>
      <li v-for="(update, index) in updates" :key="index">{{ update }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    updates: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
/* You can add scoped styles specific to this page if needed */
</style>

