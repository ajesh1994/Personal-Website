<template>
  <div class="preview">
    <g-link :to="`/blog/${article.slug}`">
      <div class="previewImage">
        <Fluid :alt="article.title" :src="article.heroImage.file.url.src" />
      </div>
      <div class="previewTitle">{{article.title}}</div>
      <p>{{article.description}}</p>
      <p />
    </g-link>
    <div class="previewDate">
      <small class="previewDate">{{article.publishDate}}</small>
    </div>
  </div>

  <!-- <template>
  <header
    id="nav"
    :class="{ 'navbar--hidden': !showNavbar, 'navbared': headerView, 'navbared2': !headerView }"
  >
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <img alt class="nav-logo" src="/logos/logo-circle-normal.svg" />
          <span style="font-size: 1.5em">HomePage Fam</span>
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
        <div class="navbar-start">
          <g-link class="navbar-item" to="/about">About</g-link>
          <g-link class="navbar-item" to="/contact">Contact</g-link>
          <hr class="navbar-divider" />
          <a class="navbar-item" href="https://github.com/kfields/gridful/issues">Report an issue</a>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <a href="https://github.com/kfields/gridful">
              <v-icon name="brands/github" scale="2" />
            </a>
          </div>
        </div>
      </div>
    </nav>
  </header>
  </template>-->
</template>


<script>
export default {
  name: "ArticlePreview",
  props: ["article"],
  components: {},
  data() {
    return {};
  }
};
</script>
<style  scoped lang="scss">
.preview {
  padding-bottom: 1rem;
}
.previewTitle {
  font-size: 1.5rem;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  // line-height: 1rem;
}
.previewImage {
  max-height: 200px;
  overflow: hidden;
  display: block;
  width: 100%;
}
.previewDate {
  text-align: right;
}

.tag {
  color: #a0a0a0;
  text-decoration: none;
  display: inline-block;
  padding: 0.33333rem 0.5rem;
  line-height: 1;
  border-radius: 2px;
  border: 1px solid #a0a0a0;
  margin-right: 0.5em;
}
</style>



