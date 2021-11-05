<template>
  <tree :data="tree" node-text="name" layoutType="horizontal" v-if="dataLoaded"> </tree>
</template>

<script>
import { tree } from "vued3tree";
import { json } from "d3";

export default {
  name: "TreeBrowser",
  components: {
    tree,
  },

  props: {
      resource_url: String,
  },

  async mounted() {
    const data = await json(
      this.resource_url
    );
    this.dataset = Object.freeze(data);
    this.dataLoaded = true
    this.tree = this.dataset
  },

  data() {
    return {
      dataset: {},
      tree: {},
      dataLoaded: false,
    };
  },
};
</script>
