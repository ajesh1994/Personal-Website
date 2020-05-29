<template>
  <div class="cardMargin">
    <g-link class="blogCardWrapper" :to="this.path">
      <div class="previewImage">
        <Fluid :alt="this.title" :src="this.image.file.url.src" />
      </div>
      <div class="previewInfo">
        <div class="previewTitle">{{this.title}}</div>
        <p class="previewDescription">{{this.description}}</p>
        <p />

        <small>
          <g-link class="readMore" :to="this.path">Read More</g-link>
        </small>
        <div class="previewDate">
          <small class="previewDate">{{this.date}}</small>
        </div>
      </div>
    </g-link>
  </div>
</template>

<script>
import marked from "marked";
export default {
  props: {
    path: String,
    date: Date,
    title: String,
    description: String,
    image: Object
  }
};
</script>
<style scoped>
.blogCardWrapper {
  display: flex;
  background: white;
  border-left: 4px solid #7510f7;
  width: 75%;
  margin: auto;
  box-shadow: 2px 2px 4px -2px rgba(0, 0, 0, 0.61);
  padding: 25px;
  flex-direction: column;
}
.readMore {
  color: #7510f7;
  font-weight: bold;
}

.previewDescription {
  margin-bottom: 30px;
}
.preview {
  padding-bottom: 1rem;
}
.previewTitle {
  font-size: 1.5rem;
  margin-top: 0.5rem;
  margin-bottom: 1.5rem;
  line-height: 1rem;
  font-family: OverpassBold;
}
.previewImage {
  max-height: 200px;
  overflow: hidden;
  display: block;
  width: 100%;
  flex: 25%;
}

.previewDate {
  text-align: right;
}
.previewInfo {
  flex: 75%;
  padding: 20px 0;
  font-family: Overpass;
}

.cardMargin {
  margin: 30px 0;
}

@media (min-width: 768px) {
  .blogCardWrapper {
    flex-direction: row;
  }

  .previewInfo {
    padding: 0 20px;
  }
}
</style>