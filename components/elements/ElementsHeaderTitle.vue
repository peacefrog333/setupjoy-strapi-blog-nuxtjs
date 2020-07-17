<template>
    <h2 v-if='content' class="mt-4 mb-4 text-2xl font-semibold text-gray-800">
        {{content.content}}
    </h2>
</template>
<script>
export default {
    name: "elements-header-title",
    props: {
        content: {
            type: Object,
            default: null
        }
    }
}
</script>