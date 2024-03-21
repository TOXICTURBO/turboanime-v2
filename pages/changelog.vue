<template>
  <div>
    <Changelog :updates="changelogUpdates" />
  </div>
</template>

<script>
import Changelog from '@/components/Changelog.vue'; // Adjust the path as needed

export default {
  components: {
    Changelog,
  },
  data() {
    return {
      changelogUpdates: [
        "Update 1: Implemented new feature",
        "Update 2: Fixed critical bug",
        // Add more updates as needed
      ],
    };
  },
};
</script>
