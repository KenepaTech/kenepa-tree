<template>
  <svg width="100%" height="100%">
      <circle v-for="(item, index) in h.descendants()"
       :key="index"
       r="5"
       :cx="item.x"
       :cy="item.y" />
  </svg>
</template>

<script>
import * as d3 from 'd3';
import { nest } from 'd3-collection';

export default {
    data() {
        return {
            width: 100,
            height: 100,
            h: d3.hierarchy({}),
            groupOrder: ['region', 'subregion'],
            dataset: []
        }
    },
    methods: {
        updateSize() {
            const {
                width,
                height
            } = this.$el.getBoundingClientRect()

            this.width = width
            this.height = height
        },
    },

    watch: {
        layout() {
            this.layout(this.h)
        },

        nestedData(val) {
            const h = d3.hierarchy(val, v => v.values)

            h.sum(v => v.value)
            h.sort((a, b) => d3.ascending(a.value, b.value))

            this.layout(h)

            this.h = h
        }
    },

    async mounted() {
        // 1. Update size
        this.updateSize()

        // 2. Load data
        const data = await d3.json('https://raw.githubusercontent.com/thegoodideaco/visualizing-hierarchies/master/datasets/populations.json')

        // 3. Apply the data as read only
        this.dataset = Object.freeze(data)
    },

    computed: {
        layout() {
            return d3.cluster()
                .size([this.width, this.height])
        },

        nester() {
            const n = nest()

            this.groupOrder.forEach(val => {
                n.key(node => node[val])
            })
            
            return n
        },

        nestedData() {
            return {
                key: 'root',
                values: this.nester.entries(this.dataset)
            }
        }
        
    }
}
</script>
