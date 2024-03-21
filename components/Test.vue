<template>
  <v-alert
    v-show="showban"
    style="position: fixed; bottom: 2.5rem; margin: auto 1.5rem; z-index: 1005"
    color="#2A3B4D"
    icon="mdi-cookie"
    title="We use cookies!"
    text="We use cookies and other tracking technologies to improve your browsing experience on our website, to analyze our website traffic, and to understand where our visitors are coming from."
  >
    <template #default>
      <br />
      <v-btn
        class="my-2 mr-1"
        variant="outlined"
        color="red"
        @click="doNottrkfn"
      >
        Disagree
      </v-btn>
      <v-btn class="my-2" color="green" @click="doTrkfn"> Agree ! </v-btn>
    </template>
  </v-alert>
</template>
