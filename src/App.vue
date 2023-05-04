<template>
  
  <div class="flex justify-center space-x-5 bg-orange-500 text-6xl mx-5 rounded-md">
      <p>datatime</p>
      <p>pname</p>
      <p>surname</p>
      <p>cn</p>
  </div>
  <p class="h-[50px]"></p>
  
  <!-- header -->
  <div class="container mx-auto ">
    <div class="grid grid-cols-4 gap-5 divide-x-4 border-solid border-2 border-green-500 rounded-md">
      <div class="text-center">
        Tag
      </div>
  
      <div class="col-span-2 text-center">
        record
      </div>
  
      <div class="text-center">
        price
      </div>
    </div>
  </div>
  <br>

  <!-- body -->
  <div class="border-solid border-2 border-green-500 rounded-md container mx-auto">
    <div v-for="task in latest"
      class="grid grid-cols-4 gap-5 divide-x-4"
    >
        <!-- tag selecize -->
        <div class="text-center">{{ task.tag }}</div>
  
        <!-- type or write -->
        <div class="col-span-2 text-center">{{ task.id }}</div>
  
        <!-- price -->
        <div class="text-center">{{ task.id }}</div>

    </div>
  </div>

  <br>
  <div class="grid grid-cols-2 container mx-auto">
    <input type="text" v-model="newTask" class="border-2 rounded-md " title="ใส่ชื่อเพื่อเพิ่ม tag ในตาราง">
    <img src="@/assets/addtask.png" class="w-[25px] h-6" @click="addTask">
  </div>
  
  <br>
  <span> {{ allTask }} </span>

  <!-- <h1>{{ title }}</h1>

  <div>
    <span>You have {{  allTask }} {{  allTask > 1 ? 'Tasks' : 'Task' }} at the monent</span>
    <br>
    <input type="text" v-model="newTask" placeholder="Add a new task">

    <button @click="addTask" :disabled="newTask.length < 1"> add new task</button>
  </div>

  <div v-if="newTask.length > 0">
    <h3>New Task preview</h3>
    <p>{{ newTask }}</p>
  </div>

  <ul>
    <li v-for="(task,index) in latest" :key="task.id">
      {{  index + 1 }}. {{  task.name }}
      
      <div v-if="task.finished">
        <button>Delete Task</button>
      </div>
      <div v-else-if="task.edit">
        <button>Edit Task</button>
      </div>
      <div v-else>
        no button
      </div>
    </li>
  </ul> -->
</template>


<script>

export default {
  data(){
    return {
      newTask: '',
      tasks: [
        { id:1 , tag: 'CC'},
        { id:2 , tag: 'HPI'},
        { id:3 , tag: 'I/O'},
      ]
    }
  },
  methods:{
    addTask(){
      if(this.newTask.length < 1) return alert('กรุณาใส่ข้อความใน tag ด้วย');

      this.tasks.push({
        id: this.tasks.length + 1,
        tag: this.newTask
      })

      this.newTask = '';
    }
  },
  computed:{
    allTask(){
      return this.tasks.length;
    },
    latest(){
      return [...this.tasks];
    }
  }
}

//   methods: {
//     addTask(){
//       if(this.newTask.length < 1) return;

//       this.tasks.push({
//         id: this.tasks.length + 1,
//         name: this.newTask,
//         finished: false
//       })

//       newTask = '';
//     },
//     finishTask(task){
//       task.finished = !task.finishTask;
//     }
//   },
//   computed: {
//     allTask(){
//       return this.tasks.length;
//     },
//     latest(){
//       return [...this.tasks].reverse();
//     }
//   }
// }
</script>