<template>
  <tree
    ref="ktree"
    :data="tree"
    node-text="name"
    layoutType="horizontal"
    v-if="dataLoaded"
    zoomable=false
    duration=0
    style="max-width: 95%;max-height: 100vh"
  >
  </tree>
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
    const data = await json(this.resource_url);
    this.dataset = Object.freeze(data);
    this.dataLoaded = true;
    this.tree = this.dataset;

    // Wait for next tick to ensure refs are loaded
    this.$nextTick(() => {
      this.$refs.ktree.$on("clickedText", (payload) => {
        const resource_url = payload.data.url;

        // Only navigate if a url is associated w/ the node
        if (resource_url) {
          window.location.href = resource_url;
        }
      });
    });
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
