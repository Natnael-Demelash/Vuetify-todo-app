<template>
  <div class="home pa-6">
    <v-text-field
      class="pa-3"
      v-model="newTaskTitle"
      @click:append="addTask"
      @keyup.enter="addTask"
      clearable
      label="Add Task"
      append-icon="mdi-plus"
    ></v-text-field>
    <p class="err pl-6" v-if="errMsg">Please Add a Task</p>
    <div class="flex">
      <v-list flat subheader three-line>
        <v-subheader>General</v-subheader>

        <div v-for="task in tasks" :key="task.id">
          <v-list-item
            @click="doneTask(task.id)"
            :class="{ 'red lighten-4': task.done }"
          >
            <template v-slot:default>
              <v-list-item-action>
                <v-checkbox :input-value="task.done"></v-checkbox>
              </v-list-item-action>

              <v-list-item-content>
                <v-list-item-title
                  :class="{ 'text-decoration-line-through': task.done }"
                  class="main-title"
                  >{{ task.title }}</v-list-item-title
                >
                <v-list-item-subtitle class="subtitle">{{
                  task.desc
                }}</v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn icon @click.stop="deleTask(task.id)">
                  <v-icon color="black lighten-1">mdi-delete-empty</v-icon>
                </v-btn>
              </v-list-item-action>
            </template>
          </v-list-item>

          <v-divider></v-divider>
        </div>
      </v-list>

      <v-spacer></v-spacer>

      <h1 class="right mr-10">Today's Task!</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: "",
      errMsg: false,
      tasks: [
        {
          id: 1,
          title: "Task 1",
          desc: "Notify me about updates to apps or games that I downloaded",
          done: false,
        },
        {
          id: 2,
          title: "Task 2",
          desc: "Notify me about updates to apps or games that I downloaded",
          done: false,
        },
        {
          id: 3,
          title: "Task 3",
          desc: "Notify me about updates to apps or games that I downloaded",
          done: false,
        },
      ],
    };
  },
  methods: {
    addTask() {
      if (this.newTaskTitle.trim() !== "") {
        let newTask = {
          id: Date.now(),
          title: this.newTaskTitle,
          done: false,
        };
        this.tasks.push(newTask);
        this.newTaskTitle = "";
      } else {
        this.errMsg = true;
      }
    },
    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
    },
    deleTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<style lang="scss" scoped>
.flex {
  display: flex;
  justify-content: center;
  align-items: center;
}
.right {
  font-size: 80px;
  color: rgba(95, 16, 95, 0.808);
}
.main-title {
  font-size: 22px;
}
.subtitle {
  font-size: 18px;
}

.err {
  color: red;
  font-size: 22px;
  font-style: italic;
}
</style>
