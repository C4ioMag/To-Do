<template>
    <div>
      <div class="header">
        <h1>TO DO</h1>
      </div>
      <div>
        <div>
            <div class="write">
                <input v-model="newTask" placeholder="Create a new task" style="width: 700px; height: 30px; border: 0px; outline: 0px; font-family: font-family: 'Courier New', Courier, monospace;;">
                 <button class="btn" @click="addTask">+</button>
            </div>
            <div class="line">
                <div class="all" v-if="showTasks">
                  <ul>
                    <li v-for="(task, index) in tasks" :key="index">
                        <label>
                            <input type="checkbox" v-model="task.completed">
                            <span :class="{ 'completed': task.completed }">{{ task.text }}</span>
                        </label>
                        <button class="btn2" @click="removeTask(index)">X</button>
                    </li>
                </ul>
                </div>
                <div class="incompleted" v-if="showTasksIncompleted">
                    <ul>
                        <li v-for="(task,index) in tasksIncompleted" :key="index">
                        <input type="checkbox" v-model="task.completed">
                        <span>{{ task.text }}</span>
                        <button class="btn2" @click="removeTask(index)"><strong>X</strong></button>
                        </li>
                    </ul>
                </div>
                <div class="done" v-if="showTasksDone">
                    <ul>
                        <li v-for="(task,index) in tasksDone" :key="index">
                        <input type="checkbox" v-model="task.completed">
                        <span class="completed">{{ task.text }}</span>
                        <button class="btn2" @click="removeTask(index)">X</button>
                        </li>
                    </ul>
                </div>
                <hr>
                <div class="foot">
                    <p>Total Tasks: {{ tasks.length }}</p>
                    <button class="btnShow" @click="showAll">All Tasks</button>
                    <button class="btnShow" @click="showIncompleted">Incompleted Tasks</button>
                    <button class="btnShow" @click="showDone">Tasks Done</button>
                    <button class="btn3" @click="clearAll(index)"> Clear All</button>
                </div>
            </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: [],
        showTasks: true,
        showTasksDone: false,
        showTasksIncompleted: false,
      };
    },
    computed: {
        tasksDone() {
            return this.tasks.filter(item => item.completed === true);
        },
        tasksIncompleted() {
            return this.tasks.filter(item => item.completed === false);
        }
    },
    
    methods: {
      addTask() {
        if (this.newTask !== '') {
          this.tasks.push({
            text: this.newTask,
            completed: false
          });
          this.newTask = '';
        }
      },
      showAll() {
       this.showTasks = true;
       this.showTasksDone = false;
       this.showTasksIncompleted = false;
      },
      showDone() {
        this.showTasks = false;
       this.showTasksDone = true;
       this.showTasksIncompleted = false;
      },
      showIncompleted() {
        this.showTasks = false;
       this.showTasksDone = false;
       this.showTasksIncompleted = true;
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      },
      clearAll(index) {
        this.tasks.splice(index)
      }
    }
  };
  </script>
  
  <style scoped>
    * {
        flex-flow: column;
    }
    .header{
        font-size: 30px;
    }
    .write {
        background-color: white;
        border-style: solid;
        border-radius: 15px;
        padding: 5px;

    }
    .btn {
        background-color: white;
        font-size: 15px;
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
        border-radius: 50%;
        margin-left: 250px;
    }
    .line {
        background-color: white;
        border-style: solid;
        border-radius: 15px;
        margin-top: 20px;
        padding: 5px;
    } 
    .btn2 {
        margin-left: 20px;
        background-color: white;
        font-size: 10px;
        border-radius: 25%;
    }
    hr {
        border: 0px;
        border-top: 1px solid black;
    }
    .btn3 {
        margin-left: 250px;
        background-color: white;
        font-size: 10px;
        border-radius: 10%;

    }
    .btnShow {
      display: flex;
      align-items: center;
      margin-left: 100px;
      background-color: white;
      border: none;
      font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }
    .foot {
        display: flex;
        flex-direction: row;
        align-items: center;
        font-size: 10px;
    }
  .completed {
    text-decoration: line-through;
    color: black;
  }
  ul {
    list-style-type: none;
    padding: 0; 
    font-size: 15px;
    font-family: 'Courier New', Courier, monospace;
  }
  </style>
  