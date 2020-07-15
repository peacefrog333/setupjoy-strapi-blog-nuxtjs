<template>
  <div>
    <div class="container mx-auto">
      <div class="px-5">
        <div class="flex flex-wrap -ml-2 mt-12 justify-center">
          <blog-post></blog-post>
          <blog-post></blog-post>
          <blog-post></blog-post>
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
  async fetch() {
    console.log(config.api.base+config.api.blogs)
    this.blogs = await axios.get(config.api.base+config.api.blogs).then((response) => {
      return response.data
    })
  },
  data() {
    return {
      seoTitle: 'Setup Joy',
      seoDescription: 'Setup Joy',
      blogs: null
    }
  }
};
</script>

<style>
</style>
