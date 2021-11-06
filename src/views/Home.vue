<template>
  <div>
    <Landing msg="Welcome to Kenepa Tree!" />
  </div>
</template>

<script>
import Landing from '@/components/Landing.vue'

export default {
  name: 'Home',
  components: {
    Landing,
  }
}
</script>