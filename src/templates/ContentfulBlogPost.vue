<template>
  <article>
    <div class="hero">
      <div class="heroImage">
        <Fluid alt :src="$page.post.heroImage.file.url.src" :width="1920" />
      </div>
    </div>
    <div class="homePage">
      <a href="/blog">Back</a>
    </div>
    <div class="section">
      <div>
        <h1>{{$page.post.title}}</h1>
        <p style="display: block">{{$page.post.publishDate}}</p>
      </div>
      <div v-html="markdown" />
    </div>
    <FootBar />
  </article>
</template>

<page-query>
query BlogPostByPath($path: String!) {
  post: contentfulBlogPost(path: $path ) {
    title
    publishDate(format: "MMMM Do, YYYY")
    description
    body
    heroImage {
      file {
        url
      }
    }
  }
}
</page-query>

<script>
import marked from "marked";
export default {
  name: "Contentful",
  data() {
    return {
      markdown: ""
    };
  },
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [{ name: "description", content: this.$page.post.description }]
    };
  },
  mounted() {
    this.$gtag.pageview({
      page_path: window.location.pathname
    });

    this.markdown = marked(this.$page.post.body);
  }
};
</script>
<style>
article ul {
  list-style: disc inside;
  margin-bottom: 1rem;
}
article ul li {
  margin-bottom: 1rem;
}

.homePage {
  padding: 24px 24px 0;
}

.homePage > a {
  color: #7510f7;
  font-size: 20px;
}
</style>