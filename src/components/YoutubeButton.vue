<template>
    <a 
        :href = "href" 
        target = "_blank" 
        class="px-3 py-2 rounded-xl border-2 mr-2 border-red-500 bg-red-500 hover:bg-red-700 hover:text-white transition-colors hover:border-red-700"
        >
        YouTube
        <slot></slot>
    </a>
</template> 

<script setup>
    const props = defineProps({
        href: String
})
</script>