<template>
  <div class="w-full sm:w-1/2 md:w-1/2 lg:w-1/3 xl:w-1/4 p-2 cursor-pointer">
    <div class="bg-white shadow-2xl rounded-lg mb-6 tracking-wide">
      <div class="md:flex-shrink-0">
        <img
          :src="blog.image.url"
          alt="mountains"
          class="w-full h-64 rounded-lg rounded-b-none"
        />
      </div>
      <div class="px-4 py-2 mt-2">
        <h2
          class="font-bold text-2xl text-gray-800 tracking-normal px-1"
        >{{blog.title}}</h2>
        <p
          class="text-sm text-gray-700 px-2 mr-1"
        >{{blog.summary}}</p>
        <div class="flex items-center justify-between mt-2 mx-6">
          <nuxt-link :to="`/blog/${blog.slug}`" class="text-blue-500 text-xs -ml-3">Show More</nuxt-link>
          <a href="#" class="flex text-gray-700">
            <svg
              fill="none"
              viewBox="0 0 24 24"
              class="w-6 h-6 text-blue-500"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z"
              />
            </svg>
            {{blog.blog_comments.length}}
          </a>
        </div>
        <div class="author flex items-center  my-3">
    
          <h2 class="text-sm tracking-tighter text-gray-900 px-2">
            <nuxt-link :to="{path: '/', query: {category: category.title}}" v-for='category in blog.blog_categories' :key='category.id' class='mr-2'>#{{category.title}}</nuxt-link>
            <span class="text-gray-600 ml-2">{{blogPostDate}}</span>
          </h2>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import moment from 'moment'
export default {
    props: {
        blog: {
            type: Object,
            default: null
        }
    },
    computed: {
        blogPostDate(){
            return moment(this.blog.created_at ).format("MMM Do YYYY")
        }
    }
};
</script>