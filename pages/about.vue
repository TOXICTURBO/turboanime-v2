<script setup>
useSeoMeta({
  ogTitle: "About",
  ogDescription: "About TurboAnime...",
  ogImage: "logo.png",
  ogUrl: "[og:url]",
  twitterTitle: "About",
  twitterDescription: "About TurboAnime...",
  twitterImage: "logo.png",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  title: "About",
});
</script>
<template>
  <v-container>
    <div style="height: fit-content; display: grid; place-items: center">
      <div class="pa-5" style="background-color: #212121">
        <h1><img src="/logo.png" alt="loho" height="50" /></h1>
        <p>
          TurboAnime is an open source anime streaming platform that offer free
          anime with no ADs and install it as Android or IOS web app. <br />
          Build with Nuxt 3, Vuetify and TurboAnime's V2 API.
        </p>
        <div class="mt-2">
          <v-btn
            class="mr-2"
            color="grey-darken-1"
            prepend-icon="mdi-github"
            href="https://github.com/TurboAnime"
          >
            Github
          </v-btn>
          <v-btn
            color="blue-darken-1"
            prepend-icon="mdi-file-document"
            href="https://turboanime.xyz"
          >
            Documentation
          </v-btn>
        </div>
        <div class="my-5">
          <h1>Donation</h1>
          We do not use ADs and rely on donation to keep the website running forever. 
          You can consider donating us to keep it alive! <br>
          <v-btn
            class="mt-4"
            color="yellow-darken-1"
            prepend-icon="mdi-cash"
            href="https://en.liberapay.com/TurboAnime"
          >
            Donation
          </v-btn>
        </div>
      </div>
    </div>
  </v-container>
</template>
