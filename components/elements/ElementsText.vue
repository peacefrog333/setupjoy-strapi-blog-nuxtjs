<template>
    <p v-if='content' class="pb-6" :class='wrapperClasses' :style='wrapperStyles'>
        {{content.content}}
    </p>
</template>
<script>
export default {
    name: "elements-text",
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