<template>

  <div>
    <a @click="editTask" href="#" class="edit_btn">&#128394;</a>
  </div>

</template>

<script>

  export default {
    name: 'Edit',
    props: {
      task: {
        type: Number
      },
      taskname: String
    },
    methods: {
      editTask() {
        this.$emit('editT', this.task)
        console.log(this.taskname + ' is being edited')
      }
    }
  }

</script>

<style scoped>

  .edit_btn {
    text-decoration: none;
    font-weight: bold;
    color: #2c3e50;
  }

</style>
