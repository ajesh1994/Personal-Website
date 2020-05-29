<template>
  <div class="cardMargin">
    <div class="blogCardWrapper" :to="this.path">
      <g-link class="previewImage" :to="this.path">
        <Fluid :alt="this.title" :src="this.image.file.url.src" />
      </g-link>
      <div class="previewInfo">
        <g-link :to="this.path">
          <div class="previewTitle">{{this.title}}</div>
        </g-link>
        <p class="previewDescription">{{this.description}}</p>
        <p />
        <small>
          <g-link class="readMore" :to="this.path">Read More</g-link>
        </small>
        <div class="previewDate">
          <small class="previewDate">{{this.date}}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
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

.readMore:hover {
  text-decoration: underline;
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
  font-family: OverpassBold;
  display: inline-block;
}

.previewTitle:hover {
  text-decoration: underline;
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
  margin-top: 10px;
}
.previewInfo {
  flex: 75%;
  padding: 20px 0 0;
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