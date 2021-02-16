<template>
  <div class="form-request">
    <input type="text" placeholder="عنوان تسک را وارد نمایید" v-model="titleTask"  v-on:keyup.enter="createTask">
    <button @click.prevent="createTask()">
      <span>
        ثبت درخواست
      </span>
    </button>
    <p class="error">
      {{error}}
    </p>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  data() {
    return {
      titleTask : '',
      error : ''
    }
  },
  components : {

  },
  methods : {
    createTask() {
      if (this.titleTask == '') {
        this.error ="لطفا عنوان تسک را وارد نمایید"
      } else {
        this.error ="";
        this.$emit('mackingTask' , this.titleTask , uuidv4());
        this.titleTask = '';
      }
    }
  }
}
</script>



<style scoped>
input {
  border: 1px solid #ccc;
  padding: 12px 8px;
  background-color: #f7f7f7;
  font-family: "aasaam-Note";
  margin-left: 8px;
}
.form-request {
  text-align: center;
} 
button {
  border: 1px solid #ccc;
  padding: 12px 8px;
  background-color: #f7f7f7;
  cursor: pointer;
}
.error {
  color: red;
}
</style>