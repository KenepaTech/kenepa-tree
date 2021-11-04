<template>
    <div>
        <input v-model.number="a">
        <input v-model.number="b">
        <h2> The sum is {{ c }}</h2>
        <h4>Reduced {{ reduced }}</h4>
    </div>
</template>

<script>
export default {
    data() {
        return {
            a: 0,
            b: 0,
            reduced: 0,
        }
    },
    computed: {
        c() {
            return this.a + this.b
        }
    },
    watch: {
        c(val) {
            this.reduced = val
            this.subtract()
        }
    },
    methods: {
        subtract() {
            this.reduced -= 0.1

            if (this.reduced > 0.001) {
                requestAnimationFrame(this.subtract)
            } else {
                this.reduced = 0
            }
        }
    }
}
</script>