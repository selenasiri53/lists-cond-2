<template>
  <header>
    <h1>Vue Lists and Conditional Content</h1>
  </header>
  <section id="app">
    <h2>Assignment</h2>
    <!-- 1) Add code to manage a list of tasks in a Vue app -->
    <!-- When clicking "Add Task" a new task with the entered text should be added -->
    <input type="text" v-model="enteredTaskValue" />
    <button @click="addTask">Add Task</button>
    <!-- 2) Output the list of tasks here -->
    <ul v-if="listIsVisible">
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <!-- 3) When the below button is pressed, the list should be shown or hidden -->
    <!-- BONUS: Also update the button caption -->
    <button @click="toggleTaskList">
      <h1>{{ buttonCaption }}</h1>
    </button>
    <!-- if goals = 0 "Add Tasks" -->
    <!-- if goals > 0, "Hide list" -->
    <!-- else "Show list" -->
  </section>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      enteredTaskValue: '',
      tasks: [],
      listIsVisible: true,
    };
  },
  computed: {
    buttonCaption() {
      return this.listIsVisible ? 'Hide List' : 'Show List';
    },
  },
  methods: {
    addTask() {
      this.tasks.push(this.enteredTaskValue);
      this.enteredTaskValue = '';
    },
    removeTask(idx) {
      this.tasks.splice(idx, 1);
    },
    toggleTaskList() {
      this.listIsVisible = !this.listIsVisible;
    },
  },
};
</script>

<style src="./styles.css" />
