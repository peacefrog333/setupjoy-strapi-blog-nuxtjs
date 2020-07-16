<template>
  <div>
    <div class="container mx-auto">
      <div class="px-5">
        <div class="flex flex-wrap -ml-2 mt-12 justify-center">
          <blog-post-card v-for='blog in blogs' :key='blog.id' :blog='blog'></blog-post-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import config  from "~/nuxt.config"
import axios from 'axios'

export default {
  head() {
    return {
      title: this.seoTitle,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.seoDescription
        },
        {
          hid: "og:title",
          name: "og:title",
          content: this.seoTitle
        },
        {
          hid: "og:description",
          name: "og:description",
          content: this.seoDescription
        },
        {
          hid: "og:site_name",
          name: "og:site_name",
          content: this.seoSiteName
        },
        {
          hid: "apple-mobile-web-app-title",
          name: "apple-mobile-web-app-title",
          content: this.seoTitle
        }
      ]
    };
  },
  watch: {
    '$route.query': '$fetch'
  },
  async fetch() {
    console.log(this.$route.query)
    let params = null
    if(this.$route.query.category){
      params = {
        'blog_categories.title': this.$route.query.category
      }
    }
    this.blogs = await axios.get(config.api.base+config.api.blogs, {params: params}).then((response) => {
      return response.data
    })
    if(this.categories.length === 0){
      this.categories = await axios.get(config.api.base+config.api.blogCategories).then((response) => {
        return response.data
      })
    }
  },
  data() {
    return {
      seoTitle: 'Setup Joy',
      seoDescription: 'Setup Joy',
      blogs: null,
      categories:  [],
    }
  }
};
</script>

<style>
</style>
