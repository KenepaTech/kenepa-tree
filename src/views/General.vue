<template>
    <TreeBrowser v-bind:resource_url="'https://raw.githubusercontent.com/KenepaTech/kenepa-tree/add-resources/data/resources.json'" />
</template>

<script>
import TreeBrowser from '@/components/TreeBrowser.vue';

export default {
    name: "General",
    components: {
        TreeBrowser,
    }
}
</script>