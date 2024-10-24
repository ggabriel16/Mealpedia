<template>
    <a 
        :href = "href" 
        target = "_blank" 
        class="px-3 py-2 rounded-xl border-2 border-transparent text-black bg-orange-500 hover:bg-orange-700 hover:text-white transition-colors"
        >
        Source
        <slot></slot>
    </a>
</template>

<script setup>
    const props = defineProps({
        href: String
 })
</script>