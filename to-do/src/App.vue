<template>
  <div class="container">
    <h2>My Vue Todo App</h2>
    <div class="writer">
      <input v-model="task" placeholder="Write task">
      <button @click="submitTask">Submit</button>
    </div>
    <div class="list">
      <table>
        <tr>
          <th>Task</th>
          <th>Status</th>
          <th>#</th>
          <th>#</th>
        </tr>
        <tr v-for="(task, index) in tasks" :key="index">
          <td :class="{'finished' : task.status === 'Finished'}">{{ task.name }}</td>
          <td style="width: 120px;" class="status" :class="{'text-danger': task.status === 'To-do',
        'text-warning': task.status === 'In progress',
        'text-success': task.status === 'Finished'
        }" @click="changeStatus(index)">{{ task.status }}</td>
          <td>
            <div class="edit" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="delete" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default{
  data(){
    return {
      task:'',
      editedTask: null,
      availableStatuses: ['To-do', 'In progress', 'Finished'],
      tasks: [
        {
          name: 'Learn to do backflip',
          status: 'To-do'
        },
        {
          name: 'Sleep 15 hours',
          status: 'In progress'
        }
      ]
    }
  },
  methods:{
    submitTask(){
      if(this.task.length === 0) return;

      if(this.editedTask === null){
        this.tasks.push({
          name: this.task,
          status: 'To-do'
        });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null
      }

      this.task = '';
    },
    
    deleteTask(index){
      this.tasks.splice(index, 1);
    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatus(index){
      let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
      if(++newIndex === 3) newIndex = 0;
      this.tasks[index].status = this.availableStatuses[newIndex];
    }
  }
};
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
    font-family: sans-serif;
}

.container{
    display: grid;
    justify-content: center;
    justify-items: center;
    margin-top: 10vh;
}

.writer{
    padding-top: 20px;
}

.writer input{
    padding: 10px;
    width: 50vh;
    outline: none;
    border-radius: 5px;
    border: 1px solid;
}

.writer button{
    padding: 10px 15px;
    color: white;
    background-color: orange;
    border-radius: 5px;
    border: 0;
}

.list{
    padding-top: 5vh;
}

table, th, td{
    border: 1px solid;
    border-collapse: collapse;
    padding: 10px 20px;
}

td{
    font-weight: 400;
}

.status{
  cursor: pointer;
}

.delete{
  cursor: pointer;
}

.edit{
  cursor: pointer;
}

.finished{
  text-decoration: line-through;
}

.text-danger{
  /* color: red; */
  color: red;
  border-color: rgba(235, 235, 235, 0.64);
}

.text-warning{
  color:yellow;
  border-color: rgba(235, 235, 235, 0.64);
}

.text-success{
  color:green;
  border-color: rgba(235, 235, 235, 0.64);
}


@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
