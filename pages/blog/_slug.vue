<template>
    <div class='container mx-auto'>
        <blog-post v-if='blog' :blog='blog'></blog-post>
        <div v-else-if='loading === false' class='text-center mt-32'>
            <div class='text-4xl'>Blog Not found</div>
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
    this.loading = true
    this.blog = await axios.get(config.api.base+config.api.blogs+"?slug="+this.$route.params.slug).then((response) => {
        this.loading = false
        return (response.data.length > 0)?response.data[0]:null
    })
  },
  computed: {
    seoTitle(){
        return this.blog ? this.blog.title : 'Setup Joy';
    },
    seoDescription(){
        return this.blog ? this.blog.summary : 'Blog not found';
    }
  },
  data() {
    return {
      blog: null,
      loading: true
    }
  }
}
</script>