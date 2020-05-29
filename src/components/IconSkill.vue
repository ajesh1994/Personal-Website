<template>
  <div class="skillBlock" id="skills">
    <div class="subHeadingWrapper">
      <h2 data-aos="fade-right" class="subHeading">Skills</h2>
      <div
        data-aos="fade-right"
        data-aos-anchor-placement="center-center"
        class="subHeadingUnderline"
      />
    </div>
    <div class="iconList">
      <div
        data-aos-anchor-placement="center-bottom"
        data-aos="zoom-in"
        class="iconWrapper"
        v-for="edge in skills.edges"
        :key="edge.node.skillName"
      >
        <img class="iconImage" :src="edge.node.iconImage.file.url.src" />
        <div class="skillName">{{ edge.node.skillName }}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    skills: Object
  },
  data() {
    return {
      hi: "e"
    };
  },
  methods: {},
  mounted() {}
};
</script>


<style scoped>
.skillBlock {
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  background: #f5f5f5;
  padding: 100px 0 50px;
}

.subHeadingWrapper {
  flex: 15%;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-bottom: 40px;
}

.subHeadingUnderline {
  border: 2px solid #7510f7;
  width: 75px;
}

.subHeading {
  font-size: 50px;
  margin-bottom: 15px;
  font-family: OverpassBold;
}
.iconList {
  display: flex;
  justify-content: space-evenly;
  flex: 50%;
  align-items: center;
  flex-wrap: wrap;
}

.iconImage {
  width: 80px;
  height: 80px;
  transform: scale(1);
  transition: all 0.2s;
}
.iconWrapper {
  flex: 50%;
  text-align: center;
  width: 150px;
  margin: 25px 0px;
}

.iconImage:hover {
  cursor: pointer;
  transform: scale(1.2);
}

.skillName {
  opacity: 0;
  transition: all 0.2s;
  margin-top: 10px;
  font-size: 30px;
  font-family: OverpassBold;
}
.iconImage:hover + .skillName {
  opacity: 1;
}

@media (min-width: 768px) {
  .skillName {
    font-size: 20px;
  }
  .subHeading {
    font-size: 66px;
  }
  .iconWrapper {
    width: 100px;
    flex: 33%;
    margin: 25px 0;
  }

  .iconImage {
    width: 70px;
    height: 70px;
  }
}

@media (min-width: 1000px) {
  .skillName {
    font-size: 30px;
  }

  .iconWrapper {
    width: 150px;
  }
  .iconImage {
    width: 80px;
    height: 80px;
  }
}
</style>