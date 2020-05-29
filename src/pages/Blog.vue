<template>
  <Layout>
    <section class="section" v-if="$page">
      <ul>
        <li v-for="{ node } in $page.posts.edges" :key="node.id">
          <BlogCard
            :path="node.path"
            :date="node.date"
            :title="node.title"
            :description="node.description"
            :image="node.heroImage"
          />
        </li>
      </ul>
      <pager class="pager" v-if="$page.posts.pageInfo.totalPages > 1" :info="$page.posts.pageInfo" />
    </section>
  </Layout>
</template>


<page-query>
  query($page: Int) {
  posts: allContentfulBlogPost(sortBy: "date", order:
  DESC, perPage: 3, page: $page) @paginate {
      totalCount pageInfo {
        totalPages
        currentPage 
      } edges { 
        node { 
          id 
          title 
          path
          description 
          date(format:"MMMM D, Y") 
          heroImage {
            file {
              url
            }
          }
          } 
        }
      }
  }
</page-query>


<script>
import { Pager } from "gridsome";
import BlogCard from "~/components/BlogCard";

export default {
  metaInfo: {
    title: "Blog"
  },
  components: {
    Pager,
    BlogCard
  }
};
</script>


<style scoped>
.pager {
  text-align: center;
}

.pager > a {
  color: #7510f7;
  padding: 10px;
  font-weight: bold;
}

.section {
  padding-top: 100px;
  /* background: #f5f5f5; */
}
</style>