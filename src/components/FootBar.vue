<template>
  <footer class="footer">
    <div class="footerInfo">
      <p>
        <!-- Made with
        <v-icon name="heart" />by
        <span>Ya boi Ajesh</span>-->
      </p>
      <div class="socialMediaWrapper">
        <a class="linkTags" href="mailto: ajeshjally@gmail.com">
          <Email class="icon" />
        </a>

        <a class="linkTags" href="https://github.com/ajesh1994/">
          <Github class="icon" />
        </a>

        <a class="linkTags" href="https://www.linkedin.com/in/ajesh-jally-61a914a7">
          <Linkedin class="icon" />
        </a>

        <a class="linkTags" href="https://www.instagram.com/ajeshjally/">
          <Instagram class="icon" />
        </a>
      </div>
      <div class="copyright">
        <v-icon name="copyright" />
        <span>Ajesh Jally, 2020</span>
      </div>

      <div class="scroll">
        <a @click="scrollToSection()" class="scrollUp">
          <v-icon name="chevron-up" class="chevronUp" />
        </a>
      </div>
    </div>
  </footer>
</template>
<script>
import "vue-awesome/icons/heart";
import "vue-awesome/icons/copyright";
import "vue-awesome/icons/chevron-up";

import Email from "vue-material-design-icons/Email.vue";
import Github from "vue-material-design-icons/Github.vue";
import Linkedin from "vue-material-design-icons/Linkedin.vue";
import Instagram from "vue-material-design-icons/Instagram.vue";
export default {
  name: "FootBar",
  props: [],
  components: {},
  data() {
    return {
      svg: ""
    };
  },
  mounted() {},
  components: {
    Email,
    Github,
    Linkedin,
    Instagram
  },
  methods: {
    scrollToSection() {
      window.scroll({
        top: 0,
        left: 0,
        behavior: "smooth"
      });
    }
  }
};
</script>
<style scoped>
.copyright {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 25px;
}
.footer {
  background: #7510f7;
  color: white;
  clip-path: polygon(50% 20%, 100% 0, 100% 100%, 0 100%, 0 0);
  padding-left: 0;
  padding-right: 0;
  height: 375px;
}
.footerInfo {
  margin-top: 100px;
  text-align: center;
  font-family: Overpass;
}
.socialMediaWrapper {
  display: flex;
  justify-content: space-between;
  width: 300px;
  margin: auto;
}

.icon {
  height: 100%;
  width: 100%;
}
.linkTags {
  border: 2px solid white;
  border-radius: 30px;
  height: 60px;
  width: 60px;
  padding: 10px;
}

.linkTags:hover .material-design-icon > .material-design-icon__svg {
  fill: #7510f7;
}
.material-design-icon > .material-design-icon__svg {
  fill: white;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
.linkTags:hover {
  background: white;
}
.material-design-icon__svg:hover {
  fill: skyblue;
}

.scroll {
  width: 120px;
  height: 50px;
  bottom: 30px;
  position: relative;

  text-align: center;
  text-decoration: none;
  margin: auto;
  margin-top: 40px;
}

.scrollUp:before {
  display: block;
  content: "";
  width: 32px;
  height: 32px;
  border: 2px solid #fff;
  background: transparent !important;
  margin: 0 0 0 -20px;
  position: absolute;
  bottom: 0;
  left: 50%;
  background: #fff;
  border-radius: 24px;
  z-index: 1;
}

.chevronUp {
  color: #fff;
  display: block;
  top: 26px;
  width: 12px;
  height: 12px;
  border-radius: 4px;
  animation: fadeInUp 1.2s linear infinite;
  position: absolute;
  left: 46px;
}
</style>