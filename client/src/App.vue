<template>
  <div id="app">
    <ImageModal :value="imageModalOpen" :image="imageModalUrl" />
    <EmailModal :value="emailModalOpen" />
    <Terminal />
  </div>
</template>

<script>
import Terminal from "./components/Terminal.vue";
import store from "./store";
import { mapState } from "vuex";
import ImageModal from "./components/ImageModal.vue";
import EmailModal from "./components/EmailModal.vue";

export default {
  name: "App",
  components: {
    Terminal,
    ImageModal,
    EmailModal
  },
  computed: mapState(["imageModalOpen", "imageModalUrl", "emailModalOpen"]),
  mounted: function() {
    store.dispatch("getCommands");
    store.dispatch("getFiles");
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 16px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: green;
  position: fixed;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  background-color: black;
  line-height: 150%;
}
input,
textarea {
  background: black;
  border: none;
  outline: none;
  color: green;
}
</style>
