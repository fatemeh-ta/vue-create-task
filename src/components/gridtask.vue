<template>
  <div>
    <ul class="tasks-list">
      <li  v-for="(task,index) in tasks" :key="task+index">
        <button @click="changestatus(task.id)" :class="{greenLine : task.color}" >
          {{ task.subject }}
          {{ task.status }}
        </button>
        <button @click="deleteTask(task.id)" class="delete">
          <i  class="fa fa-times" aria-hidden="true"></i>
        </button>
      </li>
    </ul>
    <p class="counter">تعداد تسک های تکمیل شده :
      <span> {{ counter }} </span>
    </p>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter : 0
    }
  },
  props : {
    tasks : Array
  },
  methods : {
    changestatus(id) {
      // console.log(id);
      let result = this.tasks.find(arry => arry.id === id);
      console.log(result); 
      result.status = "complete";
      result.color = !result.color;
      if(result.status === "complete" && result.color === true) {
        this.counter = this.counter + 1
      }
    },
    deleteTask(key) {
      this.tasks.splice(key , 1);
      console.log(key);
      if (this.counter > 0) {
        this.counter = this.counter -1;
      }
    }
  }
}
</script>

<style scoped>
.tasks-list li:first-child{
  display: none;
}
.tasks-list {
  list-style-type: none;
}

.tasks-list li {
  padding: 8px 0;
}
.greenLine {
  background-color: green;
  padding: 8px 12px;
  text-decoration-line: line-through;
}
.fa-times {
  padding-right: 8px;
}
.delete {
  cursor: pointer;
  background: transparent;
  border: none;
  color: red;
  padding-right: 16px;
}
.counter {
  text-align: center;
}
.counter span {
  color : red
}
</style>