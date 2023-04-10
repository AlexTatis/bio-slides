<script setup lang="ts">
    const props = defineProps<{
        data: {
            title: string,
            text: string,
            color: string
        }[],
        init: number
    }>()
</script>

<template>
    <div v-for="data in props.data">
        <div class="p-3 border-2 border-blue-400 rounded shadow-xl" v-if="init + props.data.indexOf(data) == $slidev.nav.clicks ">
            <h2 class="font-bold">{{ data.title }}</h2>
            <p v-html="data.text"></p>
        </div>
    </div>
</template>