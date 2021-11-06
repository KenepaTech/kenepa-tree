<template>
    <TreeBrowser v-bind:resource_url="'https://raw.githubusercontent.com/KenepaTech/kenepa-tree/sidebar/data/prog_lang_resources.json'" />
</template>

<script>
import TreeBrowser from '@/components/TreeBrowser.vue';

export default {
    name: "ProgLang",
    components: {
        TreeBrowser,
    }
}
</script>