<template>
    <div v-if='content' class="pb-6 my-5" >
        <div class='text-xl'>{{content.title}}</div>
        <div class='flex flex-wrap'>
            <div class='w-2/5 p-4 pl-0'>
                <img :src="content.image.url"
        class="w-full rounded-lg" />
            </div>
            <div class='w-3/5 text-base  p-4'>
            {{content.description}}
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "elements-ranking",
    props: {
        content: {
            type: Object,
            default: null
        }
    }
}
</script>