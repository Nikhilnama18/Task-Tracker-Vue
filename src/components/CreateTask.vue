<template>
  <header>
    <div class="createTask">
      Task Name:
      <input
        v-model="taskName"
        type="text"
        id="taskName"
        placeholder="Task Name"
      />
      <br />
      Task Time :
      <input
        v-model="taskTime"
        type="text"
        id="taskTime"
        placeholder="Tast Time"
      />
      <br />
      <div class="form-control form-control-check">
        Reminder
        <input
          v-model="taskReminder"
          type="checkbox"
          name="tastReminder"
          id="tastReminder"
        />
      </div>
      <div class="form-control input">
        <br /><button @click="CreateTask" id="submit">Save Task</button>
      </div>
    </div>
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "CreateTask",
  data() {
    return {
      taskName: "",
      taskTime: "",
      taskReminder: false,
    };
  },
  components: {
    Button,
  },
  methods: {
    CreateTask() {
      this.$emit("create-task", {
        text: this.taskName,
        day: this.taskTime,
        reminder: this.taskReminder,
      });
    },
  },
  emits: ["create-task"],
};
</script>

<style scoped>
.createTask {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>