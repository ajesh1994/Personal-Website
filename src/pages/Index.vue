<template>
  <Layout>
    <!-- <HeroBanner/> -->
    <main>
      <Introduction :introduction="getIntro" />
      <div class="divider" />
      <IconSkill :skills="getSkills" />
      <div class="divider1" />
      <Experience :experiences="getExperiences" />
      <div class="divider2" />
      <LatestBlogPost />
      <div class="divider3" />
      <Contact />
    </main>
  </Layout>
</template>

<script>
import HeroBanner from "~/components/HeroBanner";
import IconSkill from "~/components/IconSkill";
import Contact from "~/components/Contact";
import Experience from "~/components/Experience";
import LatestBlogPost from "~/components/LatestBlogPost";
import Introduction from "~/components/Intro";

export default {
  components: {
    HeroBanner,
    IconSkill,
    Contact,
    Experience,
    LatestBlogPost,
    Introduction
  },
  computed: {
    getSkills() {
      return this.$page.skills;
    },
    getExperiences() {
      return this.$page.experienceList.experiences;
    },
    getIntro() {
      return this.$page.intro.introductionText;
    }
  },
  mounted() {
    // console.log("Index.vue");
    // console.log(this.getSkills);
    this.$gtag.pageview({
      page_path: "Homepage"
    });
  },
  metaInfo() {
    return {
      title: "Home",
      meta: [{ name: "description", content: "Home" }]
    };
  }
};
</script>

<style scoped>
.divider {
  width: 100%;
  height: 40px;
  clip-path: polygon(0 0%, 100% 85%, 100% 100%, 0% 100%);
  background: #f5f5f5;
}
.divider1 {
  width: 100%;
  height: 40px;
  clip-path: polygon(0 0, 100% 0, 100% 0%, 0% 100%);
  background: #f5f5f5;
}

.divider2 {
  width: 100%;
  height: 40px;
  background: #f5f5f5;
  clip-path: polygon(0 0%, 100% 85%, 100% 100%, 0% 100%);
}

.divider3 {
  width: 100%;
  height: 40px;
  background: #f5f5f5;
  clip-path: polygon(0% -1%, 100% -1%, 100% 30%, 0% 100%);
}
</style>
<page-query>
query {
  skills: allContentfulIconSkill {
    edges{
      node{
        iconImage {
          path
          slug
          file {
            fileName
            url
          }
        }
        skillName
      }
    }
  },
  experienceList: contentfulExperienceList(id:"2jj6xa5b4FDbnYAadnjTpB"){
 listName,
  experiences {
    fields {
      startDate(format: "MMM YYYY"),
      companyName,
      jobTitle,
      jobDescription
    }
  }
},
    blog: allContentfulBlogPost {
      edges {
        node {
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
    },
     intro: contentfulIntroduction(id:"1H0i8l87EdAhZNa4hELs3Z") {
        	introductionText
    }
}
</page-query>
