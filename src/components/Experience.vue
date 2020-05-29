<template>
  <div class="experienceWrapper" id="experience">
    <div class="subHeadingWrapper">
      <h2 data-aos="fade-right" class="subHeading">Experience</h2>
      <div
        data-aos="fade-right"
        data-aos-anchor-placement="center-center"
        class="subHeadingUnderline"
      />
    </div>
    <div class="timeLineWrapper" data-aos="zoom-in-up">
      <ul class="timeline">
        <li class="event" v-for="jobRole in experiences" :key="jobRole.jobTitle">
          <span class="roleDate">{{jobRole.fields.startDate}}</span>
          <h3>{{jobRole.fields.companyName}}</h3>
          <h4>{{jobRole.fields.jobTitle}}</h4>
          <p>{{jobRole.fields.jobDescription}}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    experiences: Array
  },
  mounted() {
    console.log(this.experiences);
  }
};
</script>
<style scoped>
h1 {
  /* font-family: @font-title; */
  letter-spacing: 1.5px;
  font-weight: 100;
  font-size: 1.4em;
}

.timeline > h2,
h3 {
  /* font-family: @font-title; */
  letter-spacing: 1.5px;
  font-weight: 400;
  font-size: 1.4em;
  margin-top: 4rem;
}

.timeline {
  border-style: solid;
  border-width: 0px 1px 1px 4px;
  border-left: 4px solid #7510f7;
  background: whitesmoke;
  color: black;
  /* font-family: @font-text; */
  margin: 50px auto;
  letter-spacing: 0.5px;
  position: relative;
  line-height: 1.4em;
  font-size: 1.03em;
  padding: 25px;
  list-style: none;
  text-align: left;
  font-weight: 100;
  max-width: 70%;
}

.event {
  border-bottom: 1px dashed black;
  padding-bottom: 25px;
  margin-bottom: 50px;
  position: relative;
}

.event:last-of-type {
  padding-bottom: 0;
  margin-bottom: 0;
  border: none;
}

.event:before,
:after {
  position: absolute;
  display: block;
  top: 0;
}

.roleDate {
  left: -68px;
  color: black;
  font-weight: bold;
  font-size: 0.9em;
  position: absolute;
  top: -50px;
  background: white;
  border: 2px solid #7510f7;
  padding: 4px;
}

.event:after {
  box-shadow: 0 0 0 4px #7510f7;
  left: -32.85px;
  background: whitesmoke;
  border-radius: 50%;
  height: 11px;
  width: 11px;
  content: "";
  top: 5px;
}

.experienceWrapper {
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  padding: 50px 0;
}
.subHeading {
  font-size: 50px;
  margin-bottom: 15px;
  font-family: OverpassBold;
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

.timeLineWrapper {
  flex: 50%;
}

h3 {
  font-family: OverpassHeavy;
}

h4 {
  font-family: OverpassBold;
  margin-bottom: 20px;
  color: #7510f7;
}

p,
span {
  font-family: Overpass;
}
@media (min-width: 768px) {
  .timeline {
    padding: 50px;
    max-width: 50%;
  }
  .subHeading {
    font-size: 66px;
  }
  .roleDate {
    left: -150px;
    color: black;
    font-weight: bold;
    font-size: 0.9em;
    position: absolute;

    top: 0;
    background: none;
    border: none;
    padding: 0;
  }

  .event:after {
    left: -57.85px;
  }
}
</style>