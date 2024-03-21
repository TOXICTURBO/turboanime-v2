<template>
  <v-alert
    v-show="showban"
    style="position: fixed; bottom: 2.5rem; margin: auto 1.5rem; z-index: 1005"
    color="#2A3B4D"
    icon="mdi-cookie"
    title="New Update"
    text="We have a new update"
  >
    <template #default>
      <br />
      <v-btn
        class="my-2 mr-1"
        variant="outlined"
        color="red"
        @click="closePopup"
      >
        Close
      </v-btn>
        <v-btn class="my-2" color="green" @click="closePopup"> Changelog </v-btn>
    </template>
  </v-alert>
</template>

<script>
export default {
  data() {
    return {
      showban: true,
      changelogPath: '/components/changelog.vue', // Change this to your desired path
    };
  },
  methods: {
    closePopup() {
      this.showban = false;
    },
  },
};
</script>
