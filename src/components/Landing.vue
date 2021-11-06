<template>
  <div class="container">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Landing',
  props: {
    msg: String
  }
}
</script>

<style scoped>
  .container { 
    font-family: Arial, Helvetica, sans-serif;
    font-size: 48px;
    margin: 10vh auto;
    width: 350px;
    height: 200px;
    outline: dashed 1px black;
    display: flex;
    justify-content: center;
  }

  h1 {
    text-align: center;
    color: green;
  }
</style>