<template>
  <v-app dark>
    <div class="separator">
      <v-navigation-drawer>
        <Sidebar/>
      </v-navigation-drawer>

      <v-content class="div1">
        <v-container>
          <NewTask @taskAdded="addTask"/>
          <TaskGrid
              :tasks="tasks"
              @taskDeleted="deleteTask"
              @taskStateChanged="toggleTaskState"
          />
        </v-container>
      </v-content>
    </div
    >
  </v-app>
</template>


<script>
import Sidebar from "./components/Sidebar.vue";
import TaskGrid from "./components/TaskGrid.vue";
import NewTask from "./components/NewTask.vue";

export default {
  name: "App",

  components: {Sidebar, TaskGrid, NewTask},

  data() {
    return {
      tasks: [],
    };
  },
  watch: {
    tasks: {
      deep: true,
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      },
    },
  },
  methods: {
    addTask(task) {
      const sameName = (t) => t.name === task.name;
      const reallyNew = this.tasks.filter(sameName).length === 0;
      if (reallyNew || sameName === "") {
        this.tasks.push({
          name: task.name,
          pending: task.pending || true,
        });
      }
    },
    deleteTask(i) {
      this.tasks.splice(i, 1);
    },
    toggleTaskState(i) {
      this.tasks[i].pending = !this.tasks[i].pending;
    },
  },
  created() {
    const json = localStorage.getItem("tasks");
    const array = JSON.parse(json);
    this.tasks = Array.isArray(array) ? array : [];
  },
};
</script>

<style scoped>
.separator {
  width: 100%;
  display: flex;
}

.div1 {
  max-width: 1080px;
  margin: 25px 0;
  justify-content: center;
  text-align: center;
}
</style>