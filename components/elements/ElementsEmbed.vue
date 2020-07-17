<template>
    <div v-if='content' class="mt-4 mb-4 text-2xl font-semibold text-gray-800" >
        <div v-html="htmlBody"></div>
    </div>
</template>
<script>
import marked from 'marked'
export default {
    name: "elements-embed",
    props: {
        content: {
            type: Object,
            default: null
        }
    },
    computed: {
        htmlBody() {
            if (!this.content.content) return ''

            return marked(this.content.content)
        }
    }
}
</script>