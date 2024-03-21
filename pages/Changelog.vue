<script setup>
useSeoMeta({
  ogTitle: `Changelog`,
  ogDescription: `Changelog`,
  ogImage: "",
  ogUrl: useRoute().fullPath,
  twitterTitle: `Changelog`,
  twitterDescription: `Changelog`,
  twitterImage: "",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  title: "Changelog",
});
</script>

<template>
  <div>
    <Changelog :updates="changelogUpdates" />
  </div>
</template>

<script>

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
