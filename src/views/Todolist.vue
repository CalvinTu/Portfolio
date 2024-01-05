<template>
  <div class="container">
    <div class="title">
      <h1>Todo App</h1>
    </div>
    <div class="actions">
      <form @submit.prevent="addTask">
        <input type="text" placeholder="Add Task" v-model="task" required>
        <button type="submit">Add</button>
        <input type="text" placeholder="Search Task" v-model="searchQuery">
      </form>
    </div>
    <div class="tasks">
      <div
        class="task-items"
        v-for="todo in filteredTask"
        :key="todo.id"
        @click="doneTask(todo.id)"
      >
        <p :class="{ done: todo.status }">{{ todo.details }}</p>
        <button class="done-btn">Done</button>
        <button class="remove-btn" @click="removeTask(todo.id)">Remove</button>
      </div>
      <button class="clear-btn" @click="clearTask">Clear All Tasks</button>
    </div>
  </div>
</template>

<script>
  import { v4 as uuidv4 } from 'uuid';
  export default {
    data(){
      return{
        task:'',
        searchQuery: '',
        todos:[
        ]
      }
    },
    methods:{
      addTask(e) {
    e.preventDefault();
  
    // Check if the task already exists
    const taskExists = this.todos.some(task => task.details === this.task);
  
    if (taskExists) {
      // Display an error or provide feedback to the user
      // You can choose to alert, display a message, or take any other action here.
      alert('Task already exists');
    } else {
      // If the task doesn't exist, add it to the array
      const newTask = {
        id: uuidv4(),
        details: this.task,
        status: false
      };
      this.todos.unshift(newTask);
      this.task = '';
  
      // Optionally, you can provide feedback indicating that the task was added
      //alert('Task added successfully');
    }
  },
  removeTask(id) {
    const index = this.todos.findIndex(todo => todo.id === id);
  
    if (index !== -1) {
      // Ask for confirmation before removing the task
      const confirmed = window.confirm('Are you sure you want to remove this task?');
  
      if (confirmed) {
        // If the user confirms, remove the task
        this.todos.splice(index, 1);
      }
    }
  },
      doneTask(id){
        const done = this.todos.find(todo => todo.id === id);
        if (done) {
          done.status = !done.status;
        }
      },
      clearTask() {
      // Ask for confirmation before clearing all tasks
      const confirmed = window.confirm('Are you sure you want to clear all tasks?');
  
      if (confirmed) {
        // If the user confirms, clear all tasks
        this.todos = [];
      }
    }
  },
  computed: {
    allTask() {
      return this.todos.length > 0;
    },
    filteredTask() {
      return this.todos.filter(todo => {
        return todo.details.toLowerCase().includes(this.searchQuery.toLowerCase());
      });
    }
  }
  }
  </script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .container {
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 300px;
    padding: 20px;
    margin: 0 auto;
    text-align: center;
  }

  .title {
    font-size: 24px;
    margin-bottom: 20px;
  }

  .actions {
    margin-bottom: 20px;
  }

  .actions form {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .actions input[type="text"] {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
  }

  .actions button[type="submit"] {
    background-color: #3498db;
    color: #fff;
    border: 0;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
  }

  .tasks .task-items {
    display: flex;
    padding: 5px;
    border: 1px solid #ccc;
    margin: 5px;
    align-items: center;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .tasks .task-items:hover {
    background-color: #f2f2f2;
  }

  .tasks p {
    flex: 1;
    margin: 0;
    padding: 10px;
  }

  .tasks .done-btn,
  .tasks .remove-btn {
    background-color: #e74c3c;
    color: #fff;
    border: 0;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
    margin-left: 5px;
  }

  .tasks .done-btn {
    background-color: #3498db;
  }

  .tasks .clear-btn {
    background-color: #333;
    color: #fff;
    border: 0;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
    margin-left: auto;
  }

  .done {
    text-decoration: line-through;
  }
</style>
