<template>

  <div>
    <div class="aligner"><input type="text" v-model="newtask"><button @submit.prevent @click="submitTask" class="submit_btn">Добавить</button></div>
  </div>

</template>

<script>

  export default {
    name: 'New',
    props: {
      tasks: {
        type: Array
      },
      pickedid: {},
      pickedname: {}
    },
    watch: {
      pickedname: {
        immediate: true,
        deep: true,
        handler() {
          this.newtask = this.pickedname
        }
      }
    },
    data() {
      return {
        newtask: this.pickedname
      }
    },
    methods: {
      submitTask() {
        this.$emit('submitT', this.newtask)
        this.newtask = ''
      }
    }
  }

</script>

<style scoped>

  .aligner {
    text-align: center;
    margin: 1.2em auto;
  }
  .submit_btn {
    margin: 0 0 0 1em;
  }

</style>
