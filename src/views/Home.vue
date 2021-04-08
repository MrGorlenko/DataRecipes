<template>
  <div class='main'>
      <h1>Рецепты</h1>
      <router-link to='/Recipes'>
        <button class='btn btn_first'>Я знаю что ищу</button>
      </router-link>
      <a href="https://linara-khadimullina.shinyapps.io/recipes_recommender/">
          <button class='btn btn_second'>Посоветуйте мне</button>
      </a>
  </div>
</template>

<style lang="scss" scope>
    .btn{
        padding: 5px;
        border-radius: 5px;
        cursor: pointer;
        border: none;
        &:first-child{
            margin-right: 20px;
        }
        &_first{
            background-color:crimson;
            &:hover{
                background-color: darken($color: crimson, $amount: 10);
            }
        }
        &_second{
            background-color: darkorchid;
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
