<template>
  <header>
    <h1>{{ title }}</h1>
    <!-- <CreateTask @create-task="pushTask" /> -->
    <Button
      @showAddTask="showAddTask"
      :text="buttonColor()? 'Add Task' : 'Close'"
      :color="buttonColor()? 'black':'green'"
    />
  </header>
</template>
<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  data() {
    return {
      buttonCount: 1,
      text: "Add Task",
      color: "black",
    };
  },
  props: {
    title: String,
  },
  methods: {
    buttonColor() {
      if (this.buttonCount % 2 == 1) {
        return true;
      }
    },
    showAddTask() {
      this.buttonCount += 1;
      this.$emit("showAddTask");
    },
  },

  components: {
    Button,
  },
  emits: ["showAddTask"],
};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  margin-bottom: 20px;
}
</style>