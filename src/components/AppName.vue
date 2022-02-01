<template>

  <div>
    <h2>{{ appname }}</h2>
  </div>

</template>

<script>

  export default {
    name: 'AppName',
    props: { appname: String }
  }

</script>

<style scoped>

  h2 {
    text-align: center;
  }

</style>
