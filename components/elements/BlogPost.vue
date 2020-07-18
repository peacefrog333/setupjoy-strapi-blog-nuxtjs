<template>
    <div v-if='blog'>
        <div class=" px-2 md:px-0  relative w-full max-w-screen-md mx-auto mt-5 mb-4 md:mb-0" style="height: 15em;">
        <img :src="blog.image.url"
        class=" object-cover w-full h-full rounded-lg" />
        
      </div>

      <div class="max-w-screen-md px-4 mx-auto mt-5 text-lg leading-relaxed text-gray-700 lg:px-0">
          <nuxt-link :to="{path: '/', query: {category: category.title}}" 
            class="px-4 py-1 bg-transparent text-teal-600 inline-flex items-center border border-teal-600 rounded-full justify-center mb-2 mr-2 text-base" 
            v-for='category in blog.blog_categories' :key='category.id'>{{category.title}}</nuxt-link>
            <div class='text-sm'>Blog posted on {{blogPostDate}}</div>
          <h2 class="mt-2 mb-4 text-4xl font-semibold leading-tight text-gray-800">
            {{blog.title}}
          </h2>

        <component 
        v-for='item in blog.content' 
        :key='item.__component+item.id' 
        :id='item.__component+item.id' 
        :content='item' 
        :is='item.__component.replace(".", "-")' ></component>

      </div>
    </div>
</template>
<script>
import moment from 'moment'
import ElementsText from '~/components/elements/ElementsText.vue'
import ElementsImage from '~/components/elements/ElementsImage.vue'
import ElementsHeaderTitle from '~/components/elements/ElementsHeaderTitle.vue'
import ElementsEmbed from '~/components/elements/ElementsEmbed.vue'
import ElementsDivider from '~/components/elements/ElementsDivider.vue'
import ElementsRanking from '~/components/elements/ElementsRanking.vue'

export default {
    components : {
        ElementsText,
        ElementsImage,
        ElementsHeaderTitle,
        ElementsEmbed,
        ElementsDivider,
        ElementsRanking
    },
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
}
</script>