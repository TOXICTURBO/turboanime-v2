<script setup>
useSeoMeta({
  ogTitle: "Home",
  ogDescription: "TurboAnime - A streaming service for weebo...",
  ogUrl: useRoute().fullPath,
  twitterTitle: "Home",
  twitterDescription: "TurboAnime - A streaming service for weebo...",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  title: "Home",
});
</script>

<template>
  <PgCompsLandingPage />
  <PopupMessage />
</template> 

<script>
import PopupMessage from './components/popup.vue';

export default {
  components: {
    PopupMessage
  },
  // Other options and methods for your main app component
}
</script>

<style></style>
