<template>
  <div class="container">
    <h2 class="text-center mt-5">ToDo List</h2>

    <!-- Input -->
    <div class="d-flex">
     <input v-model="task" type="text" placeholder="Enter Task" class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>
    </div>

    <!--Taske Table -->

    <table class="table table-bordered mt-5">
      <thead>
      <tr>
        <th scope="col">Task</th>
        <th scope="col">Status</th>
        <th scope="col" class="text-center">#</th>
        <th scope="col" class="text-center">#</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(task, index) in tasks" :key="index">
        <td >
          <span :class="{finished: task.Status === 'finished'}">{{ task.name }}</span></td>
        <td style="width: 120px">
          <span @click="changeStatus(index)" class="pointer"
          :class="{
            'text-danger':task.Status === 'to-do',
            'text-warning':task.Status=== 'in-progress',
            'text-success':task.Status==='finished'
          }"
          >{{firstCharUpper(task.Status)}}</span></td>
        <td @click="editTask(index)">
          <div class="text-center">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td @click="deleteTask(index)">
          <div class="text-center">
            <span class="fa fa-trash" ></span>
          </div>
        </td>
      </tr>
      </tbody>
    </table>




  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      task:'',
      editedTask:null,
      availableStatuses : ['todo','in-progress','finished'],
      tasks: [
        {
          name: 'learning html',
          Status: 'to-do'
        },
        {
          name: 'eat the dinner',
          Status: 'at 9:00 pm'

        }
      ]
    }
  },
  methods:{
    submitTask(){
      console.log('hello from button');

      if (this.task.length===0)

        return;

      if(this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          Status: 'to-do'
        });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = '';
    },
    deleteTask(index){
      console.log(index)
      this.tasks.splice(index, 1);
    },
    // eslint-disable-next-line vue/no-dupe-keys
    editTask(index){
      this.task=this.tasks[index].name;
      this.editedTask = index ;
    },
    changeStatus(index){
     let newIndex = this.availableStatuses.indexOf(this.tasks[index].Status);
     if(++newIndex > 2) newIndex = 0;
     this.tasks[index].Status = this .availableStatuses[newIndex];
    },
    firstCharUpper(str){
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }
}

</script>

<style scoped>
.pointer{
  cursor: pointer;
}
.finished{
  text-decoration: line-through;
}
</style>
