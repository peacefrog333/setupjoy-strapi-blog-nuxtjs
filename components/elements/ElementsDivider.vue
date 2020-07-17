<template>
    <div v-if='content' class="border-dashed border-gray-400 border-t" >
    </div>
</template>
<script>
import marked from 'marked'
export default {
    name: "elements-divider",
    props: {
        content: {
            type: Object,
            default: null
        }
    }
}
</script>