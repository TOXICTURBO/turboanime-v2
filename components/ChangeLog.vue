<template>
  <v-alert
    v-show="showban"
    style="position: fixed; bottom: 2.5rem; margin: auto 1.5rem; z-index: 1005"
    color="#2A3B4D"
    icon="mdi-cookie"
    title="New Update"
    text="We have new update"
  >
  </v-alert>
</template>

<script>
export default {
  data() {
    return {
      showban: true,
    };
  },
  methods: {
    closePopup() {
      this.showban = false;
    },
    // Method to close the popup after a delay
    closePopupAfterDelay() {
      setTimeout(() => {
        this.closePopup();
      }, 5000); // Close after 5 seconds (adjust as needed)
    },
  },
  mounted() {
    // Automatically close the popup after a delay
    this.closePopupAfterDelay();
  },
};
</script>
