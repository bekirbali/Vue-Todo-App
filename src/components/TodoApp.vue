<template>
  <h1>Hello world {{ msg }}</h1>
  <form action="">
    <input type="text" v-model="task" />
    <button @click="onSubmit" type="submit">Submit</button>
  </form>
  <ul>
    <li v-for="(task, index) in tasks" @click="editTask" :key="index">
      <input type="checkbox" />
      <span @click="deleteTask">{{ task.name }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      tasks: [
        { name: "Learn Vue", status: false },
        { name: "Learn React", status: true },
        { name: "Learn JS", status: true },
        { name: "Learn HTML", status: true },
        { name: "Learn Tailwind CSS", status: true },
        { name: "Learn MUI", status: true },
      ],
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      this.tasks.push({ name: this.task, status: false });
      console.log(this.task);
      this.task = "";
    },
    deleteTask(e) {
      const filtered = this.tasks.filter(
        (task) => task.name !== e.target.innerText
      );
      this.tasks = filtered;
    },
    editTask(index) {
      console.log(index);
    },
  },
};
</script>
