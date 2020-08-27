<template>
  <div class="header">
    <div class="header-element">
      <img src="../assets/logo.svg" alt="" class="img_logo" />      
      <div class="header-todo">ToDo</div>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return{

    }
  }
}
</script>

<style>
  .header{
    width: 100%;
    height: 50px;
    border-bottom: 0.2px solid black;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
  }

  .header-element{
    margin-left: 50px;
    height: 100%;
    width: 150px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .img_logo{
    height: 50px;
    width: 50px;
    margin-right: 20px;
  }

  .header-todo{
    font-size: 20px;
    font-weight: 600;
  }
  
  

</style>
