<template>
  <div id="app" class="container">
    <img src="./assets/logo.png">
    <h1>ToDo tasks</h1>
    <ul class="list-group">
      <li class="list-group-item" v-for="task in tasks" :key="task.id">
        <div class="task">
          <div class="title">{{task.title}}</div>
          <span class="badge badge-light">{{task.createdDate}}</span>
        </div>
      </li>
      <li class="list-group-item" v-if="addingTask">
        <form v-on:submit.prevent>
          <div class="form-group">
            <label for="taskTitle">New task title</label>
            <input id="taskTitle" class="form-control" v-model="newTaskTitle" >
          </div>
          <div class="form-group">
            <button type="button" class="btn btn-secondary" @click="cancelNewTask">Cancel</button>
            <button type="button" class="btn btn-primary" @click="saveNewTask">Save</button>
          </div>
        </form>
      </li>
      <li class="list-group-item" v-if="!addingTask" >
        <button type="button" class="btn btn-primary" @click="showNewTask">New task</button>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'app',
  data: function() {
    return {
      counter: 0,
      tasks: [
      ],
      newTaskTitle:"",
      addingTask: false
    }
  },
  methods: {
    showNewTask: function() {
      this.addingTask = true;
    },
    cancelNewTask: function() {
      this.addingTask = false;
      this.newTaskTitle = "";
    },
    saveNewTask: function() {
      this.tasks.push( {
        id: this.counter,
        title: this.newTaskTitle,
        createdDate: new Date()
      });
      this.counter++;
      this.cancelNewTask();
    }
  },
  components: {
  }
}
</script>

<style>
</style>
