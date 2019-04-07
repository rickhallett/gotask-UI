<template>
  <q-page padding>
    <q-list highlight >
      <q-list-header>My Todos</q-list-header>
      <q-item v-for='task in tasks' :key='task.id'>
        <q-item-side icon='play_circle_filled'>
        </q-item-side>
        <q-item-main>{{ task.name }}</q-item-main>
        <q-item-side right>
          <q-item-tile>
            <q-btn color='red' icon='delete' @click='deleteTask(task.id)'></q-btn>
          </q-item-tile>
        </q-item-side>
      </q-item>
    </q-list>
    <q-input
      prefix='Add todo:'
      class='q-mt-xl'
      type='text'
      v-model='newTask.name'
    />
    <q-btn color='green' class='q-mt-xl float-right' @click='createTask'>Add todo</q-btn>
  </q-page>
</template>

<script>
export default {
  name: 'PageTodos',
  data() {
    return {
      tasks: [],
      newTask: {},
    };
  },
  created() {
    this.$axios.get('/tasks').then((response) => {
      this.tasks = response.data.items ? response.data.items : [];
    });
  },
  methods: {
    createTask() {
      if (!this.newTask.name || !this.newTask.name.trim()) {
        this.newTask = {};
        return;
      }

      // Post the new task to the /tasks route using the $http client
      this.$axios
        .put('/tasks', this.newTask)
        .then((response) => {
          this.newTask.id = response.data.created;
          this.tasks.push(this.newTask);
          this.newTask = {};
        })
        .catch((error) => {
          console.log(error);
        });
    },

    deleteTask(id) {
      this.$axios
        .delete(`/tasks/${id}`)
        .then(() => {
          this.tasks = this.tasks.filter((v) => {
            if (v.id !== id) {
              return v;
            }

            return false;
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>
