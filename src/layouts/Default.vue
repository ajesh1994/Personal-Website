<template>
  <div class="layout">
    <div class="container">
      <div class="header">
        <Articles />
        <NavBar />
      </div>
      <slot />
      <FootBar />
    </div>
  </div>
</template>
<script>
import AOS from "aos";

export default {
  mounted() {
    AOS.init({
      startEvent: "load", // name of the event dispatched on the document, that AOS should initialize on
      mirror: true,
      once: true
    });
  }
};
</script>
<style scoped>
.header {
  background: #f5f5f5;
  position: relative;
}
</style>
