<template>
    <p v-if='content' class="pb-6" >
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
    }
}
</script>