<template>
  <div class="todo">
    <div :class="todo.priority" class="prior" @click="deleteTask"></div>
    <div class="task">
      {{ todo.todo }}
    </div>
  </div>
</template>

<script>

export default {
  props: ['todo', 'index'],
  data(){
    return{
     

    }
  },
  methods: {
    deleteTask(){
      this.$emit('delTask', this.index);
    }
  }
}

</script>

<style>
  .todo{
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 40%;
    height: 30px;
    padding: 5px 10px;
  }

  .prior{
    background-color:#fff;
    border:1.5px solid #fff;    
    height:25px;
    width:25px;
    border-radius:50%;
    -moz-border-radius:50%;
    -webkit-border-radius:50%;
    margin-right: 20px;
    box-sizing: border-box;
    transition: all .3s ease-out;
  }

  .prior:hover{
    cursor: pointer;
  }

  .p1{
    border:1.5px solid red;    
  }

  .p2{
    border:1.5px solid yellow;    
  }

  .p3{
    border:1.5px solid blue;    
  }

  .p4{
    border:1.5px solid black;    
  }

  .p1:hover{
    border: 10px solid red;    
  }

  .p2:hover{
    border: 10px solid yellow;    
  }

  .p3:hover{
    border: 10px solid blue;    
  }

  .p4:hover{
    border: 10px solid black;    
  }

  .task{
    font-size: 20px;
  }

  
</style>
