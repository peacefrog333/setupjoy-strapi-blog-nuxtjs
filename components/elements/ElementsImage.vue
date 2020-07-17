<template>
    <div v-if='content' class="px-10 pb-6" :class='wrapperClasses' :style='wrapperStyles'>
        <img v-if='content.image' :src="content.image.url"
        class="text-center rounded-lg " />
        <div class='pt-2 text-sm text-center text-gray-600'>{{content.title}}</div>
    </div>
</template>
<script>
export default {
    name: "elements-image",
    props: {
        content: {
            type: Object,
            default: null
        }
    },
    computed: {
        wrapperClasses(){
            return (this.content.css) ? this.content.css.classes : ''
        },
        wrapperStyles(){
            return (this.content.styles) ? this.content.css.styles : ''
        }
    }
}
</script>