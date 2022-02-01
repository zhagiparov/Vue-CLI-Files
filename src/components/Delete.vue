<template>

  <div>
    <a @click="deleteTask" href="#" class="del_btn">&#215;</a>
  </div>

</template>

<script>

  export default {
    name: 'Delete',
    props: {
      task: {
        type: Number
      },
      taskname: String
    },
    methods: {
      deleteTask() {
        this.$emit('deleteT', this.task)
        console.log(this.taskname + ' is deleted')
      }
    }
  }

</script>

<style scoped>

  .del_btn {
    text-decoration: none;
    font-weight: bold;
    font-size: 1.5rem;
    color: #2c3e50;
  }

</style>
