<template>
  <footer class="footer">
    <p>
      Made with
      <v-icon name="heart"/>by
      <span>Ya boi Ajesh</span>
    </p>
  </footer>
</template>
<script>
import "vue-awesome/icons/heart";

export default {
  name: "FootBar",
  props: [],
  components: {},
  data() {
    return {
      svg: ""
    };
  },
  mounted() {}
};
</script>
<style>
</style>