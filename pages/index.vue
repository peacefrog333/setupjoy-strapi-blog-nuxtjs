<template>
  <div>
    <div class="container mx-auto">
      <div class="px-5">
        <div class="flex flex-wrap justify-center mt-12 -ml-2">
          <blog-post-card v-for='blog in blogs' :key='blog.id' :blog='blog'></blog-post-card>
        </div>
      </div>
    </div>
    <div v-if='loading' >
      <loading-spinner class='flex mx-auto my-2' style='margin-top: 30vh; height: 100px; width: 100px;' ></loading-spinner>
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
    let params = null
    this.loading = true
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
    this.loading = false
  },
  data() {
    return {
      seoTitle: 'Setup Joy',
      seoDescription: 'Setup Joy',
      blogs: null,
      categories:  [],
      loading: false
    }
  }
};
</script>

<style>
</style>
