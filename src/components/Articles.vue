<template>
  <div class="section">
    <marquee direction="up" scrollAmount=50><h1 class="test">{{$static.header.edges[0].node.name}}</h1></marquee>
    <marquee direction="right" scrollAmount=1000><h2>{{$static.header.edges[0].node.location}}</h2></marquee>
    <marquee scrollAmount=50><img class="hi" :src="$static.header.edges[0].node.logoImage.file.url.src" /></marquee>
  </div>
</template>
<static-query>
  query HomeQuery {
    posts: allContentfulBlogPost {
      edges {
        node {
          title
          description
          slug
          publishDate(format: "MMMM Do, YYYY")
          tags
          heroImage {
            path
            slug
            file {
              fileName
              url
            }
          }
          description
        }
      }
    }
    header: allContentfulProfileHeader {
      edges {
        node {
          location
          specialism
          name
          logoImage {
            path
            slug
            file{
              fileName
              url
            }
          }
        }
      }
    }
  }
</static-query>
<script>

export default {
  components: {
  },
};
</script>

<style scoped>
.test {
  color: red;
}
.hi {
  height: 500px;
  width: 400px;
}
</style>