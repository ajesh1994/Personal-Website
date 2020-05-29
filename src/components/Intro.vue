<template>
  <div class="intro">
    <div class="introText" data-aos="fade-down" v-html="markdown" />
    <div class="subHeadingUnderline" />
  </div>
</template>


<script>
import marked from "marked";

export default {
  props: {
    introduction: String
  },
  components: {},
  data() {
    return {
      markdown: ""
    };
  },
  mounted() {
    this.markdown = marked(this.introduction);
  }
};
</script>
<style  scoped lang="scss">
.intro {
  padding: 100px 50px 50px;
}
.subHeadingUnderline {
  border: 2px solid #7510f7;
  width: 75px;
  margin: auto;
}
.introText {
  font-family: OverpassBold;
  font-size: 20px;
  text-align: center;
  padding: 20px 0px;
}
</style>



