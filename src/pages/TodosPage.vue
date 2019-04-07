<template>
  <q-page padding>
    <!-- content -->
    <div class>
      <div class>
        <div class>
          <h2>GoTasks</h2>
          <ul class>
            <li class v-for="task in tasks" :key='task.id'>
              {{ task.name }}
              <span class>
                <button class v-on:click="deleteTask(task.id)">
                  <i class aria-hidden="true"></i>
                </button>
              </span>
            </li>
          </ul>
          <div class>
            <input
              type="text"
              class="form-control"
              placeholder="New Task"
              v-on:keyup.enter="createTask"
              v-model="newTask.name"
            >
            <span class>
              <button class type="button" v-on:click="createTask">Create</button>
            </span>
          </div>
          <!-- /input-group -->
        </div>
      </div>
    </div>
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
    // Use the vue-resource $http client to fetch data from the /tasks route
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
          console.log(this.newTask);
          this.tasks.push(this.newTask);
          this.newTask = {};
        })
        .catch((error) => {
          console.log(error);
        });
    },

    deleteTask(index) {
      // Use the $http client to delete a task by its id
      this.$axios
        .delete(`/tasks/${this.tasks[index].id}`)
        .then((response) => {
          console.log(response);
          this.tasks.splice(index, 1);
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
