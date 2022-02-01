<template>

  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <AppName appname="CRUD приложение на Vue.js" />
    <table>
      <tr>
        <th class="first_column">Дело</th>
        <th class="second_column">Статус</th>
        <th class="third_column">...</th>
        <th class="fourth_column">...</th>
      </tr>
      <tr v-for="(task, index) in tasks" :key="index">
        <td>{{ task.name }}</td>
        <td><span @click="changeStatus(index)" class="pointer">{{ task.status }}</span></td>
        <td>
          <Edit @editT="sendEdit" :task="index" :taskname="task.name" />
        </td>
        <td>
          <Delete @deleteT="deleteTask" :task="index" :taskname="task.name" />
        </td>
      </tr>
    </table>
    <New @submitT="createOrEdit" :tasks="tasks" :pickedname="newtask" :pickedid="editedTask" />
  </div>

</template>

<script>

  // @ is an alias to /src
  import AppName from '@/components/AppName.vue'
  import Delete from '@/components/Delete.vue'
  import Edit from '@/components/Edit.vue'
  import New from '@/components/New.vue'

  export default {
    name: 'Home',
    components: {
      AppName,
      Edit,
      Delete,
      New
    },

    data() {
      return {
        newtask: '',
        editedTask: null,
        availableStatuses: ['В планах', 'В процессе', 'Завершен'],
        tasks: [
          {
            name: 'Изучить Vue.js',
            status: 'В процессе'
          },
          {
            name: 'Изучить Nuxt.js',
            status: 'В процессе'
          },
          {
            name: 'Изучить Backend',
            status: 'В планах'
          }
        ]
      }
    },

    methods: {
      createOrEdit(created) {
        if (this.editedTask === null) {
          if (created === null || created === '') {
            return
          } else {
            this.tasks.push({
              name: created,
              status: 'В планах'
            })
          }
        } else {
          this.tasks[this.editedTask].name = created
          this.editedTask = null
        }
      },
      changeStatus(index) {
        let newIndex = this.availableStatuses.indexOf(this.tasks[index].status)
        if (++newIndex > 2) newIndex = 0
        this.tasks[index].status = this.availableStatuses[newIndex]
      },
      sendEdit(msg) {
        this.editedTask = msg
        this.newtask = this.tasks[msg].name
      },
      deleteTask(index) {
        this.tasks.splice(index, 1) //deleting 1 value from array
      }
    }
  }

</script>

<style scoped>

  table {
    margin: 0 auto;
    border-collapse: collapse;
  }

  th,
  td {
    padding: 0.5em;
    border: 1px solid #2c3e50;
  }

  .first_column {
    width: 15em;
  }

  .second_column {
    width: 6em;
  }

  .third_column {
    width: 1em;
  }

  .fourth_column {
    width: 1em;
  }
  .pointer {
    cursor: pointer;
  }

</style>
