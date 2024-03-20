<template>
  <div class="app">
    <!-- Modal for pop-up message -->
    <div class="modal" v-if="showPopup">
      <div class="modal-content">
        <span class="close" @click="closePopup">&times;</span>
        <h2>Welcome to Our Website!</h2>
        <p>Thank you for visiting. Enjoy your experience!</p>
      </div>
    </div>
    
    <!-- Your website content goes here -->
    <!-- For demonstration purposes, let's just add a button to open the pop-up -->
    <button @click="openPopup">Open Pop-up Message</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showPopup: false
    };
  },
  methods: {
    openPopup() {
      this.showPopup = true;
    },
    closePopup() {
      this.showPopup = false;
    }
  }
};
</script>

<style scoped>
/* Styles for modal pop-up */
.modal {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  overflow: auto;
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>
