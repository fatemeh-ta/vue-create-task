<template>
  <div id="app">
    <div class="body wrapper container">
      <Header></Header>
      <CreateTaske  @mackingTask="getTask"></CreateTaske>
      <Gridtask :tasks="tasks"></Gridtask>
      <button @click="deleteCompleted()" class="deletcompleted"> حذف تسک های تکمیل شده</button>
    </div>
  </div>
</template>

<script>
import Header from './components/header';
import CreateTaske from './components/createTask';
import Gridtask from './components/gridtask';
export default {
  data() {
    return {
      tasks : [
        {
          subject : '',
          status : 'incomplete',
          id : '',
          color : false,
        }
      ],
    }
  },
  components : {
    Header,
    CreateTaske,
    Gridtask
  },
  methods : {
    getTask(title , id) {
      this.tasks.push({ subject : title , status : 'incomplete' , id : id , color : false });
    },
    deleteCompleted() {
     this.tasks=this.tasks.filter((arry) => arry.status === "incomplete")
    },
  }
}
</script>

<style>
@import "./../node_modules/@aasaam/noto-font/dist/font-face.css";
@import "./../node_modules/font-awesome/css/font-awesome.min.css";

@font-face {
  font-family: 'FontAwesome';
  src: url('./../node_modules/font-awesome/fonts/fontawesome-webfont.eot'); /* IE9 Compat Modes */
  src: url('./../node_modules/font-awesome/fonts/fontawesome-webfont.eot') format('embedded-opentype'), /* IE6-IE8 */
       url('./../node_modules/font-awesome/fonts/fontawesome-webfont.woff2') format('woff2'), /* Super Modern Browsers */
       url('./../node_modules/font-awesome/fonts/fontawesome-webfont.woff') format('woff'), /* Pretty Modern Browsers */
       url('./../node_modules/font-awesome/fonts/fontawesome-webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
       url('./../node_modules/font-awesome/fonts/fontawesome-webfont.svg') format('svg'); /* Legacy iOS */
}

 .wrapper {
    max-width: 1200px;
    margin: 0 auto;
  }
  .body {
    border: 1px solid #000;
    padding: 8px;
    direction: rtl;
    font-family: "aasaam-Noto", sans-serif;
  }
  i {
    font-family: 'FontAwesome';
  }
  .container {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
  }
  .container::after {
    clear: both;
    content: '';
    display: table;
  }
  .deletcompleted {
    text-align: center;
    margin: 8px auto;
    display: block;
    cursor: pointer;
    border: 1px solid #ccc;
    padding: 12px 8px;
    background-color: #f7f7f7;
  }
  
</style>
