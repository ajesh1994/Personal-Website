<template>
  <div>
    <div class="headerWrapper">
      <div class="introTitle">
        <div class="introText">
          <div
            data-aos="flip-right"
            data-aos-duration="1000"
            class="leftText"
          >{{$static.header.edges[0].node.leftSideText}}</div>
          <div
            data-aos="flip-left"
            data-aos-duration="1000"
            class="rightText"
          >{{$static.header.edges[0].node.rightSideText}}</div>
        </div>
        <div class="socialMediaWrapper">
          <a class="linkTags" data-aos="fade-up" href="mailto: ajeshjally@gmail.com">
            <v-icon class="icon" name="regular/envelope" />
          </a>

          <a class="linkTags" data-aos="fade-up" href="https://github.com/ajesh1994/">
            <v-icon class="icon" name="brands/github" />
          </a>
          <a
            class="linkTags"
            data-aos="fade-up"
            href="https://www.linkedin.com/in/ajesh-jally-61a914a7"
          >
            <v-icon class="icon" name="brands/linkedin" />
          </a>

          <a class="linkTags" data-aos="fade-up" href="https://www.instagram.com/ajeshjally/">
            <v-icon class="icon" name="brands/instagram" />
          </a>
        </div>
      </div>
      <div class="imageWrapper" data-aos="zoom-in">
        <g-image class="heroImageMobile" :src="mobileImage" />
        <g-image class="heroImageDesktop" :src="desktopImage" />
      </div>
    </div>
  </div>
</template>
<script>
import "vue-awesome/icons/regular/envelope";
import "vue-awesome/icons/brands/github";
import "vue-awesome/icons/brands/linkedin";
import "vue-awesome/icons/brands/instagram";

export default {
  computed: {
    mobileImage() {
      return this.$static.header.edges[0].node.mobileLogoImage.file.url.src;
    },
    desktopImage() {
      return this.$static.header.edges[0].node.desktopLogoImage.file.url.src;
    },
    socialMediaImages() {
      return this.$static.socialMedia.edges;
    }
  },
  components: {}
};
</script>
<static-query>
  query HomeQuery {
    header: allContentfulProfileHeader {
      edges {
        node {
          leftSideText
        rightSideText
        desktopLogoImage {
          path
          slug
          file {
            fileName
            url
          }
        }
        mobileLogoImage {
          path
          slug
          file {
            fileName
            url
          }
        }
        }
      }
    }
  }
</static-query>


<style scoped>
.linkTags {
  border: 2px solid white;
  border-radius: 30px;
  height: 60px;
  width: 60px;
  padding: 10px;
}

.introText {
  display: flex;
  flex-direction: column;
  height: 60%;
  justify-content: center;
}
.imageWrapper {
  height: 45%;
  order: 1;
}
.headerWrapper {
  position: relative;
  width: 100vw;
  height: 100vh;
  background: #7510f7;
  display: flex;
  flex-direction: column;
}
.icon {
  height: 100%;
  width: 100%;
}

a > svg {
  fill: white;
  margin: auto;
}

.linkTags:hover {
  background: white;
}

.socialMediaWrapper {
  display: flex;
  justify-content: space-between;
  width: 300px;
  margin: auto;
}
.linkTags:hover > svg {
  fill: #7510f7;
}
.introTitle {
  /* position: absolute; */
  /* top: 28%;
  left: 8%; */
  height: 50%;
  display: flex;
  flex-direction: column;
  text-align: center;
  /* z-index: 1; */
  order: 2;
}
.leftText {
  font-size: 50px;
  color: white;
  font-family: OverpassHeavy;
}

.rightText {
  font-size: 50px;
  color: white;
  font-family: OverpassHeavy;
}

.heroImage {
  width: 100%;
  vertical-align: middle;
}

.heroImageMobile {
  display: block;
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.heroImageDesktop {
  display: none;
}

@media (min-width: 768px) {
  .socialMediaWrapper {
    width: 90%;
  }
  .heroImageMobile {
    display: none;
  }

  .heroImageDesktop {
    display: block;
    border-radius: 50%;
    border: 4px solid white;
  }

  .headerWrapper {
    padding: 25px;
    flex-direction: row;
  }

  .introTitle {
    position: initial;
    margin: auto;
    order: 1;
  }
  .imageWrapper {
    width: 50%;
    height: auto;
    margin: auto;
    order: 2;
  }

  .leftText {
    font-size: 66px;
    color: white;
  }

  .rightText {
    font-size: 66px;
    color: white;
  }
}

@media (min-width: 1000px) {
  .leftText {
    font-size: 80px;
  }

  .rightText {
    font-size: 80px;
  }
}
@media (min-width: 1600px) {
  .leftText {
    font-size: 130px;
  }

  .rightText {
    font-size: 130px;
  }
}

@media (min-width: 1900px) {
  .leftText {
    font-size: 160px;
  }

  .rightText {
    font-size: 160px;
  }
}
</style>