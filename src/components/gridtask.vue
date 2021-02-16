<template>
  <div>
    <ul class="tasks-list">
      <li v-for="task in tasks" :key="task.id">
        <button
          @click="changestatus(task.id)"
          :class="{ greenLine: task.complete }"
        >
          {{ task.subject }}
          {{ task.complete }}
        </button>
        <button @click="deleteTask(task.id)" class="delete">
          <i class="fa fa-times" aria-hidden="true"></i>
        </button>
      </li>
    </ul>
    <p class="counter">
      تعداد تسک های تکمیل شده :
      <span> {{ completedNum }} </span>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
    };
  },
  props: {
    tasks: Array,
  },
  computed: {
    completedNum() {
      const a = this.tasks.filter((i) => {
        return i.complete == true;
      });
      return a.length;
    },
  },
  methods: {
    changestatus(id) {
      this.$emit("changemyStatusParent", id);
    },
    deleteTask(id) {
      this.$emit("deleteMeParent", id);
    },
  },
};
</script>

<style scoped>
.tasks-list li:first-child {
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
  color: red;
}
</style>
