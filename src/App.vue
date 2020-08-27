<template>
  <div id="app">
    <Header></Header>
    <div class="add-todo">
      <select class="priority" v-model="priority" @change="focus">
        <option class="prior-options">Choose priority</option>
        <option class="prior-options">Priority 1</option>
        <option class="prior-options">Priority 2</option>
        <option class="prior-options">Priority 3</option>
        <option class="prior-options">Priority 4</option>
      </select>
      <input type="text" class="input" v-model="todo" v-on:keyup.enter="addTodo"/>
      <img src="./assets/addition.svg" alt="" class="addition_sign" @click="addTodo" />
      <div class="clear" @click="clearToDoList">All done</div>
    </div>
    <transition-group name="slide">
      <div class="todos" v-for="(todo,index) in todos" :key="index" >
        <ToDo :todo="todo" :index="index" @delTask="deleteTask"/>
      </div>
    </transition-group>
  </div>
</template>

<script>

import Header from './components/Header';
import ToDo from './components/ToDo';

export default {
  name: 'App',
  data(){
    return{
      priority: 'Choose priority',
      todo: '',
      todos: []
    }
  },
  components: {
    Header,
    ToDo
  },
  methods: {
    addTodo(){
      if(this.priority === 'Choose priority' || this.todo === ''){
        return ;
      }else{
        this.todos.push({priority: 'p'+this.priority.slice(9, 10), todo: this.todo});
        this.todos.sort((a,b) => (parseInt(a.priority.slice(1)) < parseInt(b.priority.slice(1))) ? -1 : 1);       

        this.todo = '';
        this.priority = 'Choose priority';
        document.querySelector('input').focus();
      }
    },
    deleteTask(index){
      this.todos.splice(index,1);
    },
    clearToDoList(){
      this.todos = [];
    },
    focus(){
      document.querySelector('input').focus(); 
    }
  }
}

</script>

<style>

  body{
    margin: 0;
  }

  #app {
    font-family: 'Open Sans', sans-serif;
    font-family: 'Raleway', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    overflow-x: hidden; 
  }

  .add-todo{
    display: flex;
    flex-direction: row;
    align-items: center;
    height: 50px;
    margin: 30px auto;
  }

  .addition_sign{
    width: 30px;
    height: 30px;
  }

  .addition_sign:hover{
    cursor: pointer;
  }

  .input{
    box-sizing: border-box;
    height: 30px !important;
    margin: 0 20px;
    width: 500px;
    padding: 5px 10px;
  }

  .priority{
    width: 160px;
    height: 30px;
  }

  .todos{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }


  .slide-enter-active{
    animation: slide-in 600ms ease-out forwards;
  }

  .slide-leave-active{
    animation: slide-out 600ms ease-out forwards;
        
  }

  @keyframes slide-in {
    from {
      opacity: 0;
      transform: translateX(-100%);
    }
    to {
      opacity: 1;
      transform: translateX(0);

    }
  }

  @keyframes slide-out {
    from {
      opacity: 1;
      transform: translateX(0);

    }
    to {
      opacity: 0;
      transform: translateX(100%);

    }
  }

  .clear{
    margin-left: 10px;
    text-transform: lowercase;
    padding: 5px 10px;
    border: .2px solid black;
    border-radius: 10px;
  }

  .clear:hover{
    color: white;
    background-color: black;
    cursor: pointer;
  }

  .prior-options,
  .input,
  .priority{
    font-family: 'Open Sans', sans-serif;
    font-family: 'Raleway', sans-serif;
    font-size: 19px;
    font-weight: 400;
  }


  @media only screen and (max-width: 850px){
    .add-todo{
      display: grid;
      grid-template-rows: 50% 50%;
      grid-template-columns: 50% 30% 20%;
      width: 70%;
      height: 100px;
    }

    .input{
      grid-row: 1/2;
      grid-column: 1/-1;
      margin: 0;
      width: 100%;

    }

    .priority{
      grid-row: 2/-1;
      grid-column: 1/2;
      margin: 0 auto;
    }

    .clear{
      grid-row: 2/-1;
      grid-column: 2/3;
      margin: 0 auto;
    }

    .addition_sign{
      margin: 0 auto;
    }
  }

  @media only screen and (max-width: 500px){
    .add-todo{
      width: 80%;
    }
  }

   @media only screen and (max-width: 400px){
    .add-todo{
      width: 95%;
    }
  }
</style>
