<template>
  <div class='main'>
      <h1>Recipes</h1>
      <router-link to='/Recipes'>
        <button class='btn btn_first'>I do know what I am looking for</button>
      </router-link>
      <a href="https://linara-khadimullina.shinyapps.io/recipes_recommender/">
          <button class='btn btn_second'>Advice me something!</button>
      </a>
  </div>
</template>

<style lang="scss" scope>
    .main{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .btn{
        padding: 15px;
        border-radius: 5px;
        cursor: pointer;
        border: none;
        color: #fff;
        font-weight: 600;
        margin-bottom: 22px;
        width: 260px;
        // &:first-child{
        //     // margin-right: 20px;
        // }
        &_first{
            background-color:rgb(8, 151, 15);
            &:hover{
                background-color: darken($color: rgb(8, 151, 15), $amount: 10);
            }
        }
        &_second{
            background-color: rgb(165, 9, 243);
            &:hover{
                background-color: darken($color: darkorchid, $amount: 10);
            }
        }
    }
</style>

<script>
export default {
}
</script>
