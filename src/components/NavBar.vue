<template>
  <header
    id="nav"
    :class="{ 'navbar--hidden': !showNavbar, 'navbared': headerView, 'navbared2': !headerView }"
  >
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <img alt class="nav-logo" src="../favicon.png" />
        </a>

        <a
          role="button"
          class="navbar-burger burger"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbarBasicExample"
          @click="burgerClick"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu" ref="navMenu">
        <div class="navbar-start" v-if="homePage">
          <a class="navbar-item" @click="scrollToSection('skills')">Skills</a>
          <a class="navbar-item" @click="scrollToSection('experience')">Experience</a>
          <a class="navbar-item" @click="scrollToSection('blog')">Blog</a>
          <a class="navbar-item" @click="scrollToSection('contact')">Contact</a>
        </div>
        <div class="navbar-start" v-else>
          <a class="navbar-item" href="/">Back to Homepage</a>
        </div>
      </div>
    </nav>
  </header>
</template>
<script>
import "vue-awesome/icons/brands/github";

export default {
  name: "NavBar",
  props: [],
  components: {},
  data() {
    return {
      headerView: true,
      showNavbar: true,
      lastScrollPosition: 0,
      navPostion: null,
      homePage: window.location.pathname === "/"
    };
  },
  mounted() {
    console.log(this.homePage);
    this.navPostion = window.visualViewport.height;
    //    document.onreadystatechange = () => {
    //   if (document.readyState == "complete") {
    //     console.log(document.getElementById("nav").offsetParent.getClientRects())
    //   }
    // }

    //   console.log("hi");

    //   const element = document.getElementById("nav");
    //   this.navPostion = window.screen.height;
    //   // console.log(element.offsetParent.getClientRects());
    //   // this.test();
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    scrollToSection(element) {
      document.getElementById(element).scrollIntoView({ behavior: "smooth" });
    },
    burgerClick(event) {
      const el = event.currentTarget;
      // Get the target from the "data-target" attribute
      const target = el.dataset.target;
      //const $target = document.getElementById(target);
      const $target = this.$refs["navMenu"];

      // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
      el.classList.toggle("is-active");
      $target.classList.toggle("is-active");
      $target.classList.toggle("mobile");
    },
    onScroll() {
      // const currentScrollPosition =
      //   window.pageYOffset || document.documentElement.scrollTop;
      // console.log(window.scrollY);
      // // if (currentScrollPosition < 0) {
      // //   return;
      // // }
      // // Stop executing this function if the difference between
      // // current scroll position and last scroll position is less than some offset
      // if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 60) {
      //   return;
      // }
      // this.showNavbar = currentScrollPosition < this.lastScrollPosition;
      // this.lastScrollPosition = currentScrollPosition;

      // const elementTarget = document.getElementById("nav");

      // if (window.scrollY < this.navPostion) {
      //   this.headerView = true;
      //   return;
      // }

      // if (window.scrollY > this.navPostion) {
      //   console.log(window.scrollY);
      //   console.log(this.navPostion);
      //   this.headerView = false;
      // }

      // console.log(document.getElementById("nav").getBoundingClientRect().top);
      // // console.log(this.navPostion);

      // if (document.getElementById("nav").getBoundingClientRect().top > 0) {
      //   console.log("enfiwebdiwehkd");

      //   this.headerView = true;
      //   return;
      // }

      // // if (window.scrollY > this.navPostion) {
      // //   console.log("NAV, " + this.navPostion);
      // //   console.log("WINDOW, " + window.scrollY);
      // this.headerView = false;
      // // }
      // if (Math.abs(window.scrollY - this.lastScrollPosition) < 60) {
      //   return;
      // }

      // if (this.navPostion < window.scrollY < this.navPostion + 60) {
      //   this.showNavbar = true;
      // } else {
      //   this.showNavbar = window.scrollY < this.lastScrollPosition;
      // }
      // this.lastScrollPosition = window.scrollY;

      // console.log(window.scrollY);
      // console.log(this.navPostion);

      if (window.scrollY < this.navPostion) {
        // console.log("enfiwebdiwehkd");

        this.headerView = true;
        return;
      }

      // if (window.scrollY > this.navPostion) {
      //   console.log("NAV, " + this.navPostion);
      //   console.log("WINDOW, " + window.scrollY);
      this.headerView = false;
      // }
      if (Math.abs(window.scrollY - this.lastScrollPosition) < 60) {
        return;
      }

      if (window.scrollY < this.navPostion + 60) {
        this.showNavbar = true;
      } else {
        this.showNavbar = window.scrollY < this.lastScrollPosition;
      }
      this.lastScrollPosition = window.scrollY;
    }
  }
};
</script>

<style scoped>
.navbared {
  /* height: 60px; */
  width: 100%;
  position: absolute;

  /* box-shadow: 0 2px 15px rgba(71, 120, 120, 0.5); */
  transform: translate3d(0, 0, 0);
  transition: 0.1s all ease-out;
  z-index: 10;
}

.navbared2 {
  /* background: hsl(200, 50%, 50%);

  position: fixed;
  top: 0;
  height: 60px;
  width: 100vw;
  transform: translate3d(0, 0, 0);
  transition: 0.1s all ease-out;
  z-index: 10; */

  /* height: 60px; */
  width: 100%;
  position: fixed;
  top: 0;
  /* padding-top: 60px; */
  /* bottom: -60px; */
  box-shadow: 0 2px 15px rgba(71, 120, 120, 0.5);
  transform: translate3d(0, 0, 0);
  transition: 0.1s all ease-out;
  z-index: 10;
}

.navbar--hidden {
  /* box-shadow: none; */
  transform: translate3d(0, -100%, 0);
}

.navbar {
  background: #5e07cd;
}

.navbar-item {
  color: white;
  font-size: 20px;
  font-family: OverpassHeavy;
}

.is-active {
  background: #5e07cd;
}

.nav-logo {
  border: solid 1px white;
  border-radius: 25px;
  margin: auto;
}

.navbar-burger {
  color: white;
}
.mobile a.navbar-item:hover {
  background-color: #7510f7;
  color: white;
  border: 0;
}

a.navbar-item:hover,
.navbar-link:hover {
  background-color: #7510f7;
  color: white;
  border-top: 3px solid #5e07cd;
  border-bottom: 3px solid #5e07cd;
}

.navbar-brand {
  margin-left: 3px;
}
</style>