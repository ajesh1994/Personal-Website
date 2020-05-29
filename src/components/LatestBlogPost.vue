<template>
  <div class="latestBlogWrapper" id="blog">
    <div class="subHeadingWrapper">
      <h2 data-aos="fade-right" class="subHeading">Blog</h2>
      <div
        data-aos="fade-right"
        data-aos-anchor-placement="center-center"
        class="subHeadingUnderline"
      />
    </div>
    <div class="blogInfo" data-aos="zoom-in-up">
      <p
        class="helpInfo"
      >Below is the latest blog published. If you'd like to browse all previously created blog posts please use the button below.</p>
      <BlogCard
        :path="getPath"
        :date="getDate"
        :title="getTitle"
        :description="getDescription"
        :image="getImage"
      />

      <g-link class="blogLinkButton" to="/blog/">Browse All</g-link>
    </div>
  </div>
</template>

<script>
import BlogCard from "~/components/BlogCard";
export default {
  components: {
    BlogCard
  },
  computed: {
    getDate() {
      return this.$static.blog.edges[0].node.date;
    },
    getTitle() {
      return this.$static.blog.edges[0].node.title;
    },
    getDescription() {
      return this.$static.blog.edges[0].node.description;
    },
    getImage() {
      return this.$static.blog.edges[0].node.heroImage;
    },
    getPath() {
      return this.$static.blog.edges[0].node.path;
    }
  }
};
</script>
<style scoped>
.latestBlogWrapper {
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  background: #f5f5f5;
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

.blogLinkButton {
  border: #7510f7;
  background: #7510f7;
  border-radius: 25px;
  height: 50px;
  width: 110px;
  font-size: 16px;
  color: white;
  display: block;
  margin: 20px;
  padding: 12px;
  text-align: center;
  font-family: OverpassBold;
}

.blogLinkButton:focus {
  outline: 0;
  box-shadow: 0 0 0 0.2rem #7510f7;
}

.a:focus {
  outline: 0;
}

.blogLinkButton:hover {
  background: #5e07cd;
}

.blogInfo {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.helpInfo {
  padding: 0px 50px;
  text-align: center;
  font-family: Overpass;
}

@media (min-width: 768px) {
  .helpInfo {
    padding: 0px 100px;
  }

  .subHeading {
    font-size: 66px;
  }
}
</style>

<static-query>
  query LatestBlog {
      blog: allContentfulBlogPost {
      edges {
        node {
          path,
          date(format:"MMMM D, Y"),
          title,
          description,
           heroImage {
            file {
              url
            }
          }
        }
      }
    }
  }
</static-query>