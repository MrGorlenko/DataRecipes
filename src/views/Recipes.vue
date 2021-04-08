<template>
  <div class='main'>
    <h1> Рецепты </h1>
    <div class="inputs">
        <input 
        type="text" placeholder="Я знаю название рецепта" v-model='searchRecipe'>
        <input 
        type="text" placeholder='Я знаю ингредиент' v-model='searchIngr'> 
    </div>
    <div>
      <div class='recipes'>
      <div class='recipe__instance' v-for='d in filteredData' :key=d>
        <div >
          <h2>{{d.name}}</h2>
          <img class='recipe__photo' :src="d.Photo" alt="">
          <p class='recipe__ingredients'> <span>You will need:</span> {{d.Ingredients}}</p> 
          <div>
            <p><span>Cook time:</span>  {{d.CookTime}}</p> 
            <p><span>Follow the instruction:</span>
            {{d.Directions}}</p> 
          </div> 
        </div> 
      </div>
      </div>
      
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.inputs{
    margin: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    width: 350px;
}

.main{
    input{
        display: block;
        width: 100%;
        margin-bottom: 15px;
        padding: 5px;
        border-radius: 5px;
    }
}

.recipes{
  width: 80%;
  margin: auto;

  margin-top: 20px;

  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.recipe{
  &__instance{

    display: flex;

    width: 48%;
    border: 1px solid black;
    border-radius: 5px;
    margin-bottom: 20px;
    span{
      font-weight: bold;
    }
  }
  &__photo{
    width: 95%;
    height: 300px;
    object-fit: contain;
  }

  &__ingredients{
    width: 80% ;
  }

  p, h2{
    width: 90%;
  }
}

@media (max-width: 992px) {
  .recipes{
    width: 100%;
    flex-direction: column;
  }

  .recipe{
    &__instance{
      margin: auto;
      margin-bottom: 20px;
      width: 95%;
      justify-content: center;

      justify-content: center;
    }

    &__ingredients{
      width: 100% ;
    }
  }
}
</style>

<script>
export default {
  data(){
    return {
      data: [ 
        {
   "name": "Old",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1567177.jpg",
   "Author": "Roge",
   "PrepareTime": "20 m",
   "CookTime": "1 h 30 m",
   "Ingredients": "chicken,celery,celery,carrot,onion,black pepper,chicken broth,egg,water,vegetable oil,salt,flour",
   "Directions": "In a large pot over medium heat, combine chicken, celery and their tops, carrot, onion and its peel, and pepper.  Pour broth over and bring to a boil.  Cover, reduce heat and simmer until chicken is tender and falls from the bone, about 45 minutes.**While chicken is cooking, make noodles.  In a large bowl, combine eggs, water, oil, salt and enough of the flour to make a stiff dough.**Strain chicken stock, reserving meat, celery and carrots.  Pull meat from bones and return strained stock and meat, celery and carrots to pot.  Bring to a boil.  Make noodles by cutting dough from a broth-dipped spoon or using scissors or your fingers to make small, chickpea sized, noodles and dropping them in the boiling water.  When the noodles rise to the surface they are done.**",
   "recipe_id": 22157
 },
 {
   "name": "Basmati Rice Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1025836.jpg",
   "Author": "Kristine Weatherly",
   "PrepareTime": "X",
   "CookTime": "20 m",
   "Ingredients": "water,rice,pea,cumin",
   "Directions": "In a saucepan bring water to a boil.  Add rice and stir.  Reduce heat, cover and simmer for 20 minutes.**When rice is cooked, stir in peas and cumin.  Cover and let stand for 5 minutes.**",
   "recipe_id": 22161
 },
 {
   "name": "Uglies Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/466057.jpg",
   "Author": "FOOD SEEKER",
   "PrepareTime": "20 m",
   "CookTime": "15 m",
   "Ingredients": "ground beef,onion,garlic,sauce,biscuit,cheddar",
   "Directions": "'Preheat oven to 400 degrees F (200 degrees C). Lightly grease 8 muffin cups.",
   "recipe_id": 22162
 },
 {
   "name": "Hot Bean Dip Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/5733524.jpg",
   "Author": "J. Van Liere",
   "PrepareTime": "10 m",
   "CookTime": "30 m",
   "Ingredients": "cream cheese,sour cream,bean,taco,hot pepper,parsley,green onion,cheddar,monterey jack",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**In a medium bowl, blend the cream cheese and sour cream. Mix in the refried beans, taco seasoning, hot pepper sauce, parsley, green onions, 1/2 the Cheddar cheese and 1/2 the Monterey Jack cheese. Transfer the mixture to an 8x12 inch baking dish. Top with remaining Cheddar and Monterey Jack cheeses.**Bake in the preheated oven 20 to 30 minutes, until cheese is slightly browned.**",
   "recipe_id": 22163
 },
 {
   "name": "Tuna with Pear Salsa Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Betty Crocker®",
   "PrepareTime": "10 m",
   "CookTime": "5 m",
   "Ingredients": "pear,pepper,green onion,cilantro,lemon,lemon juice,salt,tuna",
   "Directions": "Make Pear Salsa. Mix all ingredients in small glass or plastic bowl. Cover and refrigerate at least 1 hour to blend flavors but no longer than 24 hours.**Set oven control to broil. Spray broiler pan rack with cooking spray. Place fish on rack in broiler pan. Broil with tops about 4 inches from heat about 5 minutes or until fish flakes easily with fork. Top with salsa.**",
   "recipe_id": 22167
 },
 {
   "name": "Slow Cooker Barbecue Beans Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/565205.jpg",
   "Author": "TJACKSON",
   "PrepareTime": "15 m",
   "CookTime": "6 h",
   "Ingredients": "ground beef,bacon,onion,bake,bean,lima bean,ketchup,1 tablespoon liquid smoke flavoring,salt,sauce,garlic",
   "Directions": "Place beef in a large, deep skillet. Cook over medium high heat until evenly brown. Drain and set aside.**Place bacon in a large, deep skillet. Cook over medium high heat until evenly brown. Drain and set aside.**In a slow cooker combine ground beef, bacon, onion, baked beans, kidney beans, lima beans, ketchup, liquid smoke, salt, hot sauce and garlic powder.  Cook on low for 4 to 6 hours.**",
   "recipe_id": 22170
 },
 {
   "name": "Waffles I Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/3875444.jpg",
   "Author": "OneShyOfABunch",
   "PrepareTime": "5 m",
   "CookTime": "15 m",
   "Ingredients": "egg,flour,milk,vegetable oil,white sugar,baking powder,salt,vanilla",
   "Directions": "Preheat waffle iron. Beat eggs in large bowl with hand beater until fluffy.  Beat in flour, milk, vegetable oil, sugar, baking powder, salt and vanilla,  just until smooth.**Spray preheated waffle iron with non-stick cooking spray. Pour mix onto hot waffle iron. Cook until golden brown. Serve hot.**",
   "recipe_id": 22180
 },
 {
   "name": "Rice with Goodies Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/990527.jpg",
   "Author": "DOREENF",
   "PrepareTime": "15 m",
   "CookTime": "30 m",
   "Ingredients": "water,rice,bacon,onion,celery,carrot,pea,mushroom,almond,raisin,apple,turkey,chicken,soy sauce,parsley,black pepper",
   "Directions": "In a medium saucepan bring water to a boil. Add rice and stir. Reduce heat, cover and simmer for 20 minutes.**Place bacon in a large, deep skillet. Cook over medium high heat until evenly brown.**Mix the onion, celery, carrot, peas, mushrooms, almonds, raisins and apple into the skillet. Slowly cook and stir over medium heat until tender.**Mix in the turkey, chicken soup base, soy sauce, parsley and pepper. Mix in the rice. Serve hot.**",
   "recipe_id": 22189
 },
 {
   "name": "Blueberry Coffee Cake II Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/813693.jpg",
   "Author": "ZIPITY",
   "PrepareTime": "20 m",
   "CookTime": "45 m",
   "Ingredients": "flour,baking powder,salt,vegetable oil,white sugar,egg,milk,blueberry,flour,white sugar,cinnamon,butter",
   "Directions": "Preheat oven to 375 degrees F (190 degrees C). Grease and flour a 9 inch pan. Sift together the flour, baking powder and salt. Set aside.**In a large bowl, whisk together the oil, sugar and egg. Stir in the flour mixture alternately with the milk, mixing just until incorporated.  Fold in the blueberries. Pour batter into prepared pan. Cover with streusel topping.**For the topping:  In a bowl, combine 1/3 cup flour, cinnamon and 1/2 cup sugar.  Cut in the butter until mixture resembles coarse crumbs.**Bake in the preheated oven for 45 minutes, or until a toothpick inserted into the center of the cake comes out clean. Allow to cool.**",
   "recipe_id": 22194
 },
 {
   "name": "Zippy Egg Casserole Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/4381962.jpg",
   "Author": "ANY14TNS",
   "PrepareTime": "15 m",
   "CookTime": "1 h 10 m",
   "Ingredients": "sausage,1 (5.5 ounce) package seasoned croutons,cheddar,swiss cheese,cheese,egg,cream,milk,mustard,onion,pepper",
   "Directions": "Place sausage in a large, deep skillet. Cook over medium-high heat until evenly brown. Drain, crumble, and set aside.**In a lightly greased 9x13 inch baking dish, arrange the croutons in a single layer. Layer with Cheddar cheese, Swiss cheese, and pepperjack cheese. Top with the cooked sausage.**In a large bowl, beat together the eggs, half-and-half, milk, mustard, onion, salt, and pepper. Pour into the dish over the sausage. Cover, and refrigerate overnight.**The next morning, bake in an oven preheated to 350 degrees F (175 degrees C) for 45 to 60 minutes. Let sit for 20 minutes before serving.**",
   "recipe_id": 22196
 },
 {
   "name": "Cereal Treats II Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/24385.jpg",
   "Author": "SHELLYGIRL814",
   "PrepareTime": "2 m",
   "CookTime": "3 m",
   "Ingredients": "butter,marshmallow,cereal",
   "Directions": "Grease a 9x13 inch pan with butter or cooking spray.**In a large microwave safe bowl, combine butter and marshmallows. Microwave on high for 1 to 2 minutes, stirring every 30 seconds, until smooth. Remove from the oven and stir in the cereal.**Press in to the prepared pan with the back of a buttered spoon. Let the treats cool for about 2 hours until set. Cut into squares and serve.**",
   "recipe_id": 22203
 },
 {
   "name": "Oven Barbecued Beef Brisket II Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/2692050.jpg",
   "Author": "MARCIA ELLIS",
   "PrepareTime": "5 m",
   "CookTime": "4 h",
   "Ingredients": "brisket,cola,onion,chile",
   "Directions": "Preheat oven to 325 degrees F (165 degrees C).**In a roasting pan, place brisket fat side up. In a small bowl, combine cola beverage, onion soup mix, and chile sauce. Pour chile sauce mixture over brisket.**Cover, and bake in preheated oven for 3 to 4 hours. Uncover the brisket during the last hour of cooking.**",
   "recipe_id": 22204
 },
 {
   "name": "Parmesan Dijon Chicken Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/980737.jpg",
   "Author": "Betty Crocker®",
   "PrepareTime": "10 m",
   "CookTime": "30 m",
   "Ingredients": "butter,mustard,bread,parmesan,chicken",
   "Directions": "Preheat oven to 375  degrees F.  Mix butter and mustard in shallow dish until well mixed. Mix bread crumbs and cheese in large plastic bag.**Dip one piece of chicken at a time into butter mixture, coating all sides. Then place in bag of bread crumbs, seal bag and shake to coat with crumb mixture. Place chicken in single layer in ungreased 9x13 inch baking dish.**Bake uncovered 20 to 30 minutes, turning once, until juice of chicken is no longer pink when centers of thickest pieces are cut.**",
   "recipe_id": 22206
 },
 {
   "name": "Orange Pineapple Slushie Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/26155.jpg",
   "Author": "CK",
   "PrepareTime": "5 m",
   "CookTime": "X",
   "Ingredients": "orange juice,pineapple,white sugar,ice",
   "Directions": "In a blender, combine orange juice, pineapple, sugar and ice cubes. Blend on low until there are no more chunks of ice.  Blend on high until smooth and frothy.  Pour into 2 glasses and serve.**",
   "recipe_id": 22211
 },
 {
   "name": "Oaty Cereal Bars Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/187834.jpg",
   "Author": "TJACKSON",
   "PrepareTime": "10 m",
   "CookTime": "5 m",
   "Ingredients": "white sugar,honey,peanut butter,cereal,peanut",
   "Directions": "Grease a 9x13 inch pan. In a large saucepan over medium heat, stir together the sugar and honey. Bring to a boil, then remove from heat and stir in the peanut butter until well blended. Stir in the cereal and if desired, stir in the salted peanuts. Press into the prepared pan. Allow to cool until firm, then cut into bars.**",
   "recipe_id": 22212
 },
 {
   "name": "Tiger Butter Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/28623.jpg",
   "Author": "annnn",
   "PrepareTime": "1 m",
   "CookTime": "3 m",
   "Ingredients": "chocolate,chocolate,peanut butter,cereal",
   "Directions": "Line a 9x9 inch dish with waxed paper.**Combine white chocolate, chocolate chips and peanut butter in a 2 quart microwave safe dish and microwave on low one minute.  Stir until smooth.  Stir in the rice cereal and spread into prepared pan.  Let cool completely before cutting into squares.**",
   "recipe_id": 22213
 },
 {
   "name": "Chrusciki II Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "shirleyo",
   "PrepareTime": "5 m",
   "CookTime": "20 m",
   "Ingredients": "butter,egg,sugar,sour cream,vinegar,rum,flour,fry,sugar",
   "Directions": "'In a medium bowl, mix together the butter, yolks, sugar, sour cream, vinegar and rum until smooth. Gradually stir in flour until the dough is thick enough to handle. Turn the dough out onto a lightly floured surface and knead for about 15 minutes. Put the dough into a bowl and cover with a cloth. Let it rest in a cool place for an hour.**Heat oil in heavy skillet to 375 degrees F (190 degrees C). To test readiness of oil, put a small piece of dough in it, if it immediately comes to the surface, the temperature is right. On a lightly floured surface, roll the dough out to no thicker than 1/8 inch thickness. Cut into strips 2 inches wide and 7 inches long. Cut a 2 inch slit down the center of the strip lengthwise. Pull one end through the hole.**Fry 4 or 5 strips at a time, turning once, until brown. Drain on paper towels and dust with confectioners'' sugar while still warm.**'",
   "recipe_id": 22215
 },
 {
   "name": "'Grampa''s Brandy Alexander Recipe '",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/864033.jpg",
   "Author": "Leslie",
   "PrepareTime": "5 m",
   "CookTime": "X",
   "Ingredients": "brandy,cacao,chocolate,chocolate",
   "Directions": "In blender, combine brandy, creme de cacao, and chocolate syrup. Blend at medium speed until well-mixed.  Add the softened ice cream in large chunks. Blend at high speed until smooth. Serve immediately.**",
   "recipe_id": 22218
 },
 {
   "name": "Peking Pork Chops Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/687851.jpg",
   "Author": "Lynda McCormick",
   "PrepareTime": "15 m",
   "CookTime": "6 h",
   "Ingredients": "pork chop,brown sugar,ginger,soy sauce,ketchup,garlic,pepper",
   "Directions": "Trim excess fat from pork chops and place in slow cooker.  Mix brown sugar, ginger, soy sauce, ketchup, garlic, salt and pepper in small bowl and pour over meat.  Cover, turn to low and cook 4 to 6 hours, or until tender.  Season with salt and pepper, if needed.**",
   "recipe_id": 22219
 },
 {
   "name": "Creamy Caramel Flan Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/3233797.jpg",
   "Author": "Jo Poynor",
   "PrepareTime": "15 m",
   "CookTime": "1 h 15 m",
   "Ingredients": "white sugar,cream cheese,egg,milk,milk,vanilla",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**In a small, heavy saucepan over medium-low heat, cook sugar, stirring, until golden.  Pour into a 10 inch round baking dish, tilting to coat bottom and sides.  Set aside.**In a large bowl, beat cream cheese until smooth.  Beat in eggs, one at a time, until well incorporated.  Beat in condensed and evaporated milk and vanilla until smooth.  Pour into caramel coated pan.  Line a roasting pan with a damp kitchen towel.  Place baking dish on towel, inside roasting pan, and place roasting pan on oven rack.  Fill roasting pan with boiling water to reach halfway up the sides of the baking dish.**Bake in preheated oven 50 to 60 minutes, until center is just set.  Cool one hour on wire rack, then chill in refrigerator 8 hours or overnight.  To unmold, run a knife around edges of pan and invert on a rimmed serving platter.**",
   "recipe_id": 22220
 },
 {
   "name": "PJ Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "ADWANA",
   "PrepareTime": "20 m",
   "CookTime": "X",
   "Ingredients": "grains,apple juice,cherry,drinks,water,apple,orange,grape,strawberry,lemon,lime",
   "Directions": "In a 5 gallon container, combine grain alcohol, pineapple juice, cherry juice, drink mix powder and water. Add apples, oranges, grapes, strawberries, lemons and limes. Stir gently and serve.**",
   "recipe_id": 22223
 },
 {
   "name": "Easy and Elegant Pork Tenderloin Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/602402.jpg",
   "Author": "Susan Burget",
   "PrepareTime": "10 m",
   "CookTime": "35 m",
   "Ingredients": "bread,olive,pork tenderloin",
   "Directions": "Preheat oven to 425 degrees F (220 degrees C).**Mix bread crumbs and olive oil in bowl to reach consistency that would be moist enough to stick to the meat when pressed.  Place pork on a shallow cooking sheet.  Press the crumb mixture onto all sides of the meat until there is no pink showing, usually 1/4 inch thick.**Bake for at least 35 minutes until a meat thermometer reads 165 degrees F (75 degrees C) or until there is no pink when the pork is cut.  Let the pork rest for 10 minutes, then cut into 1/2 inch slices.**",
   "recipe_id": 22224
 },
 {
   "name": "Stuffed Chicken Breasts with Gouda and Spinach Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/975770.jpg",
   "Author": "Betty Crocker®",
   "PrepareTime": "20 m",
   "CookTime": "55 m",
   "Ingredients": "cheese,nutmeg,spinach,chicken,salt,pepper,margarine",
   "Directions": "To Make Smoked Gouda-Spinach Stuffing: Combine all stuffing ingredients. Mix together.**Preheat oven to 375  degrees F. Grease square pan, 9x9x2 inches.**Remove bones from chicken breasts. Do not remove skin. Loosen skin from chicken breasts.**Make desired stuffing. Spread one-fourth of the stuffing evenly between meat and skin of each chicken breast. Smooth skin over breasts, tucking under loose areas. Place chicken, skin sides up, in pan. Sprinkle with salt and pepper. Drizzle with margarine.**Bake uncovered 45 to 55 minutes or until juice of chicken is no longer pink when centers of thickest pieces are cut.**",
   "recipe_id": 22226
 },
 {
   "name": "Salty Dog I Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/5450307.jpg",
   "Author": "Leslie A.",
   "PrepareTime": "1 m",
   "CookTime": "X",
   "Ingredients": "fruit juice,salt,vodka",
   "Directions": "Fill a highball glass with ice then pour in grapefruit juice, salt and vodka. Mix well and serve.**",
   "recipe_id": 22227
 },
 {
   "name": "Gator Smoothies Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/4484482.jpg",
   "Author": "Ashley",
   "PrepareTime": "5 m",
   "CookTime": "X",
   "Ingredients": "ice,drinks,ice cream",
   "Directions": "In a blender, combine ice, sports drink and ice cream. Blend until smooth. Pour into glasses and serve.**",
   "recipe_id": 22229
 },
 {
   "name": "Pistachio Cream Dessert Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/277186.jpg",
   "Author": "Karen",
   "PrepareTime": "20 m",
   "CookTime": "X",
   "Ingredients": "pistachio,milk,cream,white sugar,chocolate,chocolate",
   "Directions": "Prepare pudding with milk as directed on package.  Chill in refrigerator.**Whip cream with sugar until stiff peaks form.  Fold one-quarter of whipped cream into pudding.**In a 9x13 inch dish, spread a thin layer of pudding mixture.  Top with a layer of wafers.  Spread one-third of whipped cream over wafers.  Sprinkle one-third of crushed candy over whipped cream.  Repeat layers until all ingredients are used.  Chill 2 hours before serving.**",
   "recipe_id": 22232
 },
 {
   "name": "Coffee Nudge Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/987334.jpg",
   "Author": "MADAMMOCHA",
   "PrepareTime": "1 m",
   "CookTime": "10 m",
   "Ingredients": "coffee,liqueur,brandy,cacao,cream,chocolate",
   "Directions": "In the bottom of 8 coffee mugs, pour 1 ounce each coffee liqueur and brandy. Pour in 1/2 ounce each  creme de cacao. Fill each cup with hot coffee and garnish with a dollop of whipped cream and chocolate sprinkles.**",
   "recipe_id": 22233
 },
 {
   "name": "Caponatax Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/986642.jpg",
   "Author": "Betty Crocker®",
   "PrepareTime": "20 m",
   "CookTime": "15 m",
   "Ingredients": "olive,onion,garlic,eggplant,tomato,basil,red wine,salt,pepper",
   "Directions": "Heat oil in 10-inch nonstick skillet over medium heat.  Cook onion and garlic in oil about 3 minutes, stirring occasionally, until onion is tender.**Stir in eggplant and tomato.  Cook uncovered 8 to 10 minutes, stirring frequently, until eggplant is very tender.  Stir in remaining ingredients.**Cover and refrigerate about 2 hours or until cool.  Garnish with fresh oregano if desired.**",
   "recipe_id": 22235
 },
 {
   "name": "Super Easy Chicken Manicotti   Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Betty Crocker®",
   "PrepareTime": "20 m",
   "CookTime": "1 h 30 m",
   "Ingredients": "tomato,garlic,chicken,14 uncooked manicotti shells,olive,mozzarella",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Spread about 1/3 of the pasta sauce in ungreased 9x13 inch baking dish.**Sprinkle garlic salt on chicken. Insert chicken into uncooked manicotti shells, stuffing from each end of shell to fill if necessary. Place shells on pasta sauce in dish.**Pour remaining 2/3 pasta sauce evenly over shells, covering completely. Sprinkle with olives and cheese.**Cover and bake in the preheated oven for about 1 1/2 hours, or until shells are tender.**",
   "recipe_id": 22236
 },
 {
   "name": "Strawberry Margarita Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/36408.jpg",
   "Author": "Jeremy Ward",
   "PrepareTime": "15 m",
   "CookTime": "25 m",
   "Ingredients": "cake,egg,water,vegetable oil,strawberry,lime,topping thawed",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 9x13-inch pan.**In a large bowl, stir together cake mix, egg whites, oil, water and margarita mix. Pour batter into prepared pan. Bake in the preheated oven for 25 minutes, or until a toothpick inserted into the center of the cake comes out clean. Allow to cool.**Stir lime zest into the Cool Whip(R). Frost cooled cake and refrigerate until serving.**",
   "recipe_id": 22237
 },
 {
   "name": "Chocolate Oat Squares Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/101328.jpg",
   "Author": "Janea",
   "PrepareTime": "30 m",
   "CookTime": "25 m",
   "Ingredients": "butter,brown sugar,egg,vanilla,oat,flour,baking soda,salt,milk,butter,chocolate,salt,walnut,vanilla",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease a 9x13 inch pan.**In a medium bowl, cream together 1 cup butter with brown sugar until smooth. Beat in the eggs and 2 teaspoons vanilla. Stir in the oats, flour, baking soda and 1 teaspoon  of salt. Press two thirds of the mixture into the bottom of the prepared pan. Set aside remaining dough.**In a large saucepan over medium heat, combine the condensed milk, 2 tablespoons of butter, chocolate chips and remaining 1/2 teaspoon of salt. Stir frequently until melted and smooth. Remove from the heat and stir in walnuts and remaining 2 teaspoons of vanilla. Spread over the prepared crust and sprinkle with the reserved crust mixture.**Bake in the preheated oven for 25 minutes, or until golden brown. Cool completely before cutting into squares.**",
   "recipe_id": 22243
 },
 {
   "name": "Frying Pan Okra Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1997508.jpg",
   "Author": "sal",
   "PrepareTime": "5 m",
   "CookTime": "15 m",
   "Ingredients": "butter,onion,okra,tea",
   "Directions": "Melt butter in a medium saucepan over medium heat and saute onion until translucent.  Stir in okra and turmeric.  Reduce heat to low and cook 15 minutes, or until tender.**",
   "recipe_id": 22244
 },
 {
   "name": "Oyster Shooters Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1060516.jpg",
   "Author": "Lindsay",
   "PrepareTime": "5 m",
   "CookTime": "X",
   "Ingredients": "oyster,tomato,horseradish,pepper,vodka,lemon",
   "Directions": "In a mixing bowl, combine tomato juice, horseradish and pepper. Mix thoroughly. Cut the lemon into 6 wedges.**Pour 1/2 shot of tomato juice mixture into a small glass. Add a shot of vodka. Put 1 raw oyster in the glass and garnish with lemon wedge.**",
   "recipe_id": 22255
 },
 {
   "name": "Tequila Shrimp Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/377618.jpg",
   "Author": "Michael",
   "PrepareTime": "10 m",
   "CookTime": "10 m",
   "Ingredients": "butter,garlic,shrimp,tequila,cilantro,pepper",
   "Directions": "Melt butter in a large skillet over medium heat. Saute garlic until light brown. Place shrimp in the pan, and cook for 3 minutes.**Pour in tequila, and season with cilantro, salt, and pepper. Cook for 2 more minutes.**",
   "recipe_id": 22256
 },
 {
   "name": "Roast Loin of Pork Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1006481.jpg",
   "Author": "Karen Fazio",
   "PrepareTime": "15 m",
   "CookTime": "2 h",
   "Ingredients": "roast,garlic,white wine,lemon juice,olive,onion,bay leaf,thyme,salt,black pepper",
   "Directions": "Make slits in the roast and insert garlic slices. Combine in a large plastic bag: wine, lemon juice, olive oil, onions, bay leaves, thyme, salt and pepper.  Add roast and marinate overnight in refrigerator.**Preheat oven to 350 degrees F (175 degrees C). Remove meat from marinade and roast until meat is no longer pink inside and a thermometer reads 145 degrees F (63 degrees C).**",
   "recipe_id": 22258
 },
 {
   "name": "Mocha Cake V Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/1324.jpg",
   "Author": "PIANOJEN8",
   "PrepareTime": "10 m",
   "CookTime": "45 m",
   "Ingredients": "cake,vanilla,vegetable oil,sour cream,egg,liqueur,chocolate,chocolate,butter",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 10 inch Bundt pan.**In a large bowl, stir together cake mix and pudding mix. Make a well in the center and pour in oil, sour cream and eggs. Beat on low speed until blended. Scrape bowl, and beat 4 minutes on medium speed. Stir in the coffee liqueur and chocolate chips.**Pour batter into prepared pan. Bake in the preheated oven for 45 minutes, or until a toothpick inserted into the center of the cake comes out clean. Allow to cool.  Spread with Chocolate Glaze.**For Chocolate Glaze:    In a saucepan, melt together the butter and chocolate chips, stirring frequently.  Cool slightly, then quickly spoon over cake.**",
   "recipe_id": 22259
 },
 {
   "name": "Raspberry Peach Chicken Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Betty Crocker®",
   "PrepareTime": "5 m",
   "CookTime": "20 m",
   "Ingredients": "raspberry,peach,brandy,honey,salt,black pepper,chicken",
   "Directions": "To Broil: Set oven control to broil. Spray broiler pan rack with cooking spray.**Place raspberries, peach slices, brandy and honey in blender or food processor. Cover and blend on high speed about 1 minute or until smooth. Heat blended mixture in 1-quart saucepan. Keep warm.**Sprinkle both sides of chicken with salt and pepper.**Place chicken on rack in broiler pan. Broil with tops 4 to 6 inches from heat 15 to 20 minutes, turning once, until juice is no longer pink when centers of thickest pieces are cut.**Spoon some of the raspberry sauce on serving plate. Place chicken on sauce. Drizzle with additional sauce. Garnish with additional raspberries if desired.**To Grill:  Brush grill rack with vegetable oil. Heat grill to medium heat. Place chicken on grill rack or on rack in broiler pan. Cover and grill 4 to 6 inches from heat 15 to 20 minutes, turning once, until juice is no longer pink when centers of thickest pieces are cut.Brush grill rack with vegetable oil. Heat grill to medium heat. Place chicken on grill rack or on rack in broiler pan. Cover and grill 4 to 6 inches from heat 15 to 20 minutes, turning once, until juice is no longer pink when centers of thickest pieces are cut.**",
   "recipe_id": 22260
 },
 {
   "name": "Pot Roast for Many Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/4515322.jpg",
   "Author": "Jim Kleinhans",
   "PrepareTime": "15 m",
   "CookTime": "2 h 30 m",
   "Ingredients": "roast,margarine,onion,garlic,white sugar,brown sugar,gravy,potato,carrot,water",
   "Directions": "Preheat oven to 325 degrees F (165 degrees C).**Lightly coat the beef chuck roast with margarine. Sprinkle onion salt, garlic salt, white and brown sugar and one package of gravy mix over the roast.**In a large roasting pan, spread a layer of potatoes and carrots on the bottom of the pan. Sprinkle 2/3 package of the gravy mix over the potato layer. Place the prepared roast on the bottom layer of potatoes and carrots. Surround the roast with the remaining potatoes and carrots, and sprinkle on the remaining gravy mix.  Add the remaining margarine and the water to the pan.**Cover and bake in the preheated oven for 30 minutes. Reduce temperature to 300 degrees F (150 degrees C) and continue baking for 2 hours and 15 minutes, or to desired doneness.**",
   "recipe_id": 22261
 },
 {
   "name": "Greek Honey Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/812903.jpg",
   "Author": "'Jan O''Leary Merzlak'",
   "PrepareTime": "30 m",
   "CookTime": "40 m",
   "Ingredients": "flour,baking powder,salt,cinnamon,orange,butter,white sugar,egg,milk,walnut,white sugar,honey,water,lemon juice",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 9 inch square pan. Combine the flour, baking powder, salt, cinnamon and orange rind. Set aside.**In a large bowl, cream together the butter and 3/4 cup sugar until light and fluffy. Beat in the eggs one at a time.  Beat in the flour mixture alternately with the milk, mixing just until incorporated. Stir in the walnuts.**Pour batter into prepared pan. Bake in the preheated oven for 40 minutes, or until a toothpick inserted into the center of the cake comes out clean. Allow to cool for 15 minutes, then cut into diamond shapes.  Pour honey syrup over the cake.**For the Honey Syrup:      In a saucepan, combine honey, 1 cup sugar and water.  Bring to a simmer and cook 5 minutes.  Stir in lemon juice, bring to a boil and cook for 2 minutes.**",
   "recipe_id": 22262
 },
 {
   "name": "Apple Sheet Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/4114462.jpg",
   "Author": "Barbara",
   "PrepareTime": "30 m",
   "CookTime": "30 m",
   "Ingredients": "pastry,flour,baking powder,salt,shortening,milk,apple,apple,white sugar,cinnamon,flour,butter,FROSTING:,sugar,milk,butter,vanilla",
   "Directions": "'Preheat oven to 400 degrees F (200 degrees C). In a large bowl, combine 3 cups flour, baking powder and salt. Cut in shortening to the consistency of coarse crumbs. Stir in 1 cup cold milk slowly until completely blended. Separate dough into two balls. Roll out one ball of dough to fit a 15 x 10 inch pan with some dough extending over the edge of the pan.**In a large bowl, combine sliced apples, sugar, cinnamon and 2 tablespoons flour. Place filling in an even layer over prepared crust. Thinly slice 1/2 cup butter and evenly distribute over the apples. Roll out the remaining dough and place over the apple filling. Seal edges and prick the top all over with a fork.**Bake in the preheated oven for 30 minutes. Cool 5 minutes before frosting.**To make the frosting:  In a small bowl, combine confectioners'' sugar, 3 tablespoons milk, 1/3 cup butter and vanilla extract. Beat until smooth and creamy.**'",
   "recipe_id": 22265
 },
 {
   "name": "'Grandma''s Carrot Cake Recipe '",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/5858698.jpg",
   "Author": "heybejay",
   "PrepareTime": "40 m",
   "CookTime": "45 m",
   "Ingredients": "flour,baking soda,cinnamon,white sugar,vegetable oil,egg,vanilla,walnut,pineapple,carrot,coconut,butter,white sugar,buttermilk,vanilla",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease a 9x13 inch pan. Sift together the flour,  baking soda and cinnamon. Set aside.**In a large bowl, combine the sugar and oil until blended.  Beat in the eggs one at a time, then stir in the vanilla. Stir in the flour mixture just until incorporated.  Fold in the pineapple, carrots, coconut and walnuts.  Pour batter into prepared pan.**Bake in the preheated oven for 45 minutes, or until a toothpick inserted into the center of the cake comes out clean.  While still warm, poke holes in the cake with a fork.**For the glaze:  In a saucepan, combine butter, sugar, buttermilk and vanilla.  Bring mixture to a boil over medium heat, then reduce heat and cook for 5 minutes.  Pour glaze over warm cake, then allow to cool completely.**",
   "recipe_id": 22266
 },
 {
   "name": "Rich Mocha Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "mghordlo",
   "PrepareTime": "25 m",
   "CookTime": "40 m",
   "Ingredients": "flour,baking powder,milk,shortening,white sugar,egg,vanilla,water,white sugar,coffee,whipped topping mix",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 9x13-inch pan.**Sift together the flour, baking powder and powdered milk. Set aside.**Cream together shortening and sugar until light and fluffy. Beat in eggs, one at a time, then stir in the vanilla. Stir in the flour mixture until incorporated. Batter will be thick.**Pour batter into prepared pan. Bake in the preheated oven for 40 minutes, or until a toothpick inserted into the center of the cake comes out clean. Prick cake with a fork at 1 inch intervals. Allow to cool.**For the glaze: In a saucepan, combine the sugar, water and instant coffee.  Bring mixture to a boil, and cook for 2 minutes. Pour the syrup over the warm cake. Cool thoroughly. Prepare whipped topping according to package directions, then frost cake. Refrigerate for 3 hours or overnight before serving.**",
   "recipe_id": 22269
 },
 {
   "name": "Sparkling Grilled Ham Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/10168.jpg",
   "Author": "Andrew",
   "PrepareTime": "20 m",
   "CookTime": "30 m",
   "Ingredients": "grape,orange juice,brown sugar,vegetable oil,red wine,mustard,ginger,clove,ham",
   "Directions": "Combine grape juice, orange juice, brown sugar, oil, vinegar, mustard, ginger and cloves.  Slash fat on edge of ham.  Pour mixture over ham in a shallow glass dish.  Refrigerate overnight or 2 hours at room temperature.  Baste with mixture occasionally.**Grill over low coals 15 minutes each side, basting frequently with mixture.**",
   "recipe_id": 22272
 },
 {
   "name": "Artichoke Pie Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/72161.jpg",
   "Author": "Lisa Bianco",
   "PrepareTime": "10 m",
   "CookTime": "45 m",
   "Ingredients": "olive,garlic,artichoke,bread,parmesan,bake,egg,mozzarella",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**Heat oil in a large skillet over medium heat.  Saute garlic until it starts to brown.  Stir in the artichoke hearts and cook 10 minutes before adding the bread crumbs and half of the parmesan cheese.  When heated through, transfer half of artichoke mixture to pie crust.**Pour eggs over artichoke mixture and sprinkle in the rest of the parmesan cheese.  Spoon the rest of the artichoke mixture into the pie and top with mozzarella cheese.**Bake in preheated oven for 45 minutes, or until crust begins to brown.**",
   "recipe_id": 22274
 },
 {
   "name": "Crazy Mixed Up Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/447154.jpg",
   "Author": "Dana Hall",
   "PrepareTime": "10 m",
   "CookTime": "30 m",
   "Ingredients": "flour,brown sugar,cocoa powder,baking soda,salt,vegetable oil,vinegar,vanilla,milk,chocolate",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour an 8 inch square pan. Combine the flour, brown sugar, cocoa powder, baking soda and salt in prepared pan.  Mix well with a fork.**Make three \"wells\" in the dry ingredients. Pour oil in the first, vinegar in the second, and vanilla in the third. Pour milk over the top and mix all ingredients with a fork until well blended. Pour chocolate chips over the top.**Bake in the preheated oven for 30 minutes, or until a toothpick inserted into the center of the cake comes out with moist crumbs.  Cool in pan for 15 minutes, then cut and serve directly from the pan.**",
   "recipe_id": 22275
 },
 {
   "name": "Caramel Apple Pie III Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/2612809.jpg",
   "Author": "sal",
   "PrepareTime": "20 m",
   "CookTime": "50 m",
   "Ingredients": "caramel,flour,ice cream,pecan,lemon juice,apple,bake",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**Unwrap and cut caramel candy in half. In a large bowl, mix candy with flour. Stir in apples, ice cream topping, and lemon juice. Pour filling into pie crust and sprinkle with chopped pecans.**Place in oven on a sheet of foil to catch the drips. Bake in preheated oven for 50 minutes, or until golden and bubbly.**",
   "recipe_id": 22277
 },
 {
   "name": "Easy Fruit Cobbler Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/884797.jpg",
   "Author": "Kristin",
   "PrepareTime": "10 m",
   "CookTime": "40 m",
   "Ingredients": "blueberry,cake,lemon",
   "Directions": "Preheat oven to 375 degrees F (190 degrees C). Grease a 9x13 inch pan.**Spread pie filling over the bottom of the prepared pan, then sprinkle evenly with the cake mix.  Pour lemon-lime soda over the top.  Bake in preheated oven for 45 minutes.**",
   "recipe_id": 22278
 },
 {
   "name": "Black Bottom Cupcakes II Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1002291.jpg",
   "Author": "SHERIMA1",
   "PrepareTime": "10 m",
   "CookTime": "20 m",
   "Ingredients": "flour,baking soda,cocoa powder,salt,white sugar,vegetable oil,water,vinegar,vanilla,cream cheese,egg,white sugar,salt,chocolate",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Line two 12 cup muffin pans with paper liners. Sift together the flour, baking soda, cocoa powder and salt.  Set aside.**In a large bowl, whisk together 1 cup sugar, oil and water until blended.  Stir in the vinegar and vanilla.  Beat in the flour mixture until incorporated.  Set aside.**In a medium bowl, beat together the cream cheese, egg, 1/3 cup sugar and salt.  Stir in the chocolate chips.**Fill muffin cups 1/3 full with chocolate batter, then top with a heaping tablespoon of the cream cheese mixture.  Bake in the preheated oven until the tops spring back when lightly pressed, 20 to 25 minutes.**",
   "recipe_id": 22281
 },
 {
   "name": "Raspberry Sour Cream Pie Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/2399107.jpg",
   "Author": "Cathy M.",
   "PrepareTime": "20 m",
   "CookTime": "40 m",
   "Ingredients": "bake,egg,sour cream,vanilla,white sugar,salt,flour,raspberry,brown sugar,flour,walnut,butter",
   "Directions": "Preheat oven to 400 degrees F (200 degrees C).**In a large bowl, beat eggs until light and lemon colored. Whisk in sour cream and vanilla. In a separate bowl, mix sugar, flour and salt together. Stir into egg mixture. Gently fold in raspberries. Pour filling into 2 unbaked pie crusts.**Bake the pies without the topping in the preheated oven for 30 to 35 minutes, or until the center begins to set.**While pies bake, make the topping: In a medium bowl, mix together brown sugar, flour and chopped nuts. Cut in butter until crumbly. Set aside.**Sprinkle pies with topping and return to oven for 10 to 15 minutes, or until topping is golden brown. Allow to cool before serving.**",
   "recipe_id": 22282
 },
 {
   "name": "Shoofly Pie V Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/627709.jpg",
   "Author": "FORDER1",
   "PrepareTime": "30 m",
   "CookTime": "30 m",
   "Ingredients": "molasses,baking soda,water,salt,flour,brown sugar,butter,cinnamon,bake",
   "Directions": "Preheat oven to 375  degrees F (190 degrees C).**In a medium bowl, dissolve the soda in the molasses and stir until it foams. Sir in the boiling water and pinch of salt. In a separate bowl, mix the flour, cinnamon, brown sugar and butter into crumbs.**Pour 1/3 of the molasses mixture into the unbaked crust. Sprinkle 1/3 of the crumbs over the molasses mixture and continue alternating layers, finishing with the crumbs on top.**Bake in preheated oven for 30 minutes, or until the crumbs and crust are golden.**",
   "recipe_id": 22285
 },
 {
   "name": "Shredded Beef Enchiladas Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1807631.jpg",
   "Author": "Christy Campbell",
   "PrepareTime": "45 m",
   "CookTime": "1 h 30 m",
   "Ingredients": "roast,water,beef,red wine,chili,cumin,onion,chile pepper,flour,sour cream,monterey jack,fry,tortillas",
   "Directions": "Place roast in a large saucepan that has a tight-fitting lid. Pour in water, cover, and simmer on low for 30 minutes. Increase heat to medium/high, and brown the roast on all sides. Once the water has boiled away, pour in the beef broth, vinegar, chili powder and 1 tablespoon of cumin. Cover tightly and reduce heat to low. Simmer for 1 1/2 to 2  hours or until the beef falls apart when you try to pick it up.  Shred  the beef, using 2 forks or your fingers. Place shredded beef back into the saucepan with all the juices, and let cool to room temperature.**In a large skillet, saute the onion until just soft, not browned. Mix in flour and green chilies. Stir constantly for 2 minutes to cook the flour taste out. Stir in sour cream and 2 cups of Monterey Jack cheese. Cook on low for 10 minutes, stirring often, until the cheese is all melted and mixed. Set aside and let cool.**In a large heavy skillet, heat the olive oil. Using tongs dip the tortillas, one at a time, into the oil for 30 seconds each side. Drain on paper towels.**Preheat oven to 375  degrees F (190 degrees C). Spread 4 tablespoons of sour cream mixture down the center of the tortilla. Top with about the same amount of beef.  Roll up and place seam side down in one or two 8x11 inch baking dish.  Repeat for each tortilla. Continue until you are out of the filling. Sprinkle with remaining Monterey Jack cheese.**Bake in a pre-heated oven for 30 minutes or until cheese is melted and bubbling.**",
   "recipe_id": 22286
 },
 {
   "name": "Tasty Green Beans Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/62944.jpg",
   "Author": "CAROLCHIU",
   "PrepareTime": "15 m",
   "CookTime": "30 m",
   "Ingredients": "green bean,margarine,onion,garlic,soy sauce,beef,water,pepper",
   "Directions": "Bring a large pot of water to a boil.  Add green beans and cook for 5 minutes. Drain and rinse with cold water.**Melt margarine in a large saucepan over high heat.  Mixing well, add green beans, onions and garlic.  Stir in soy sauce.  While stirring, add bouillon and water.  Reduce heat to low and simmer, stirring occasionally, for 20 minutes.  Season with salt and pepper to taste.**",
   "recipe_id": 22289
 },
 {
   "name": "Peppermint Punch Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/325715.jpg",
   "Author": "OKLAQUILTER",
   "PrepareTime": "5 m",
   "CookTime": "X",
   "Ingredients": "ice cream,milk,ginger",
   "Directions": "Place ice cream in a punch bowl, and allow to soften slightly. Blend in milk and ginger ale. Stir until frothy. Serve at once, or keep chilled until ready to serve.**",
   "recipe_id": 22290
 },
 {
   "name": "Turkey Delight Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/688953.jpg",
   "Author": "Ann Orwig",
   "PrepareTime": "15 m",
   "CookTime": "1 h",
   "Ingredients": "turkey,bread,potato,turkey",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**Bring a large pot of salted water to a boil.  Add potatoes and cook until tender but still firm, about 15 minutes. Drain and mash.**Prepare stuffing as directed.**Place the stuffing in a 2 quart baking dish. Layer with turkey and cover with 1 cup gravy. Top with mashed potatoes and the remaining gravy.**Bake covered in the preheated oven 45 minutes, or until bubbly and lightly browned.**",
   "recipe_id": 22291
 },
 {
   "name": "Turkey Pot Pie III Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1052140.jpg",
   "Author": "MANEY42",
   "PrepareTime": "15 m",
   "CookTime": "45 m",
   "Ingredients": "bake,mushroom,turkey,vegetable,milk",
   "Directions": "Preheat oven to 400 degrees F (200 degrees C). Place one pie crust in an ungreased pie dish.**In a medium bowl, mix the mushroom soup and milk. Stir in the turkey meat and mixed vegetables. Pour the mixture into the pie crust in the dish. Top with the other pie crust, and seal the crust edges by crimping with a wet fork.**Bake in the preheated oven 45 minutes, or until the crust is golden brown**",
   "recipe_id": 22292
 },
 {
   "name": "Orzo with Mushrooms and Walnuts Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/241546.jpg",
   "Author": "Amanda Dattilio",
   "PrepareTime": "10 m",
   "CookTime": "25 m",
   "Ingredients": "walnut,olive,onion,mushroom,chicken broth,pasta,pepper",
   "Directions": "Preheat the oven to 350 degrees F (175 degrees C). Place walnuts on a baking sheet. Bake for 8 to 10 minutes in the preheated oven, or until they release their aroma. Stir once or twice for even toasting.**Heat oil in a large heavy saucepan over medium-high heat.  Saute onion and mushrooms until tender and golden brown.**Pour in broth, and bring to a boil. Stir in orzo, reduce heat to low, and cover. Simmer until orzo is tender and liquid is absorbed, about 15 minutes.  If after 15 minutes there is still liquid, remove cover, and cook until liquid is gone. Remove from heat, and stir in walnuts.  Season with salt and pepper to taste.**",
   "recipe_id": 22293
 },
 {
   "name": "Sunset Cooler Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Louise",
   "PrepareTime": "20 m",
   "CookTime": "40 m",
   "Ingredients": "sugar,water,2 pandan leaves,pineapple,water,cinnamon,clove",
   "Directions": "To Make the Basic Syrup:  Place sugar, 1 cup water and pandan leaves in a deep saucepan. Bring to a boil, lower heat and simmer until sugar is dissolved. Remove pandan leaves and strain the syrup. Allow to cool for use as a basic syrup. Store the syrup in a bottle in the refrigerator.**To Make the Cooler:  In a blender or food processor, puree the pineapple chunks. Strain and reserve the juice.**In a deep saucepan, combine the pineapple pulp, 1 1/2 cups water, cinnamon stick and cloves. Bring to a boil, then reduce heat and simmer for 20 minutes. Remove from heat, strain and discard pulp and spices. Allow the reserved liquid to cool.**In a pitcher, combine spiced pineapple syrup and reserved pineapple juice. Stir in enough cooled Basic Syrup to sweeten to your taste. Chill in refrigerator.**To serve, pour into glasses full of crushed ice.**",
   "recipe_id": 22294
 },
 {
   "name": "Yellow Squash and Zucchini Delight Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/820595.jpg",
   "Author": "KINGSLADY",
   "PrepareTime": "15 m",
   "CookTime": "25 m",
   "Ingredients": "zucchini,yellow squash,cabbage,onion,chicken broth",
   "Directions": "In a large pot place zucchini, yellow squash, cabbage and onion.  Pour broth over vegetables and bring to a boil over medium heat.  Reduce heat to low, cover and simmer for 20 to 30 minutes.**",
   "recipe_id": 22296
 },
 {
   "name": "Melt In Your Mouth Pork Chops Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/2801751.jpg",
   "Author": "JOANBISHTON",
   "PrepareTime": "20 m",
   "CookTime": "1 h 20 m",
   "Ingredients": "soy sauce,sauce,water,pork chop",
   "Directions": "In a large bowl combine soy sauce, teriyaki sauce and water.**In a large skillet on medium heat, brown both sides of the pork chops in a small amount of oil. Pour liquid mixture over chops. Add more water if needed. Chops should be covered completely in liquid.**Bring to a boil. Lower temperature and simmer for an hour and twenty minutes, turning chops over half way through.**",
   "recipe_id": 22297
 },
 {
   "name": "'Cha Cha''s White Chicken Chili Recipe '",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/631578.jpg",
   "Author": "Cathy",
   "PrepareTime": "10 m",
   "CookTime": "20 m",
   "Ingredients": "vegetable oil,onion,garlic,pepper,chile pepper,cumin,oregano,pepper,chicken broth,chicken,bean,monterey jack",
   "Directions": "Heat the oil in a large saucepan over medium-low heat. Slowly cook and stir the onion until tender. Mix in the garlic, jalapeno, green chile peppers, cumin, oregano and cayenne. Continue to cook and stir the mixture until tender, about 3 minutes. Mix in the chicken broth, chicken and white beans. Simmer 15 minutes, stirring occasionally.**Remove the mixture from heat. Slowly stir in the cheese until melted. Serve warm.**",
   "recipe_id": 22302
 },
 {
   "name": "Antojitos Minis Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/2435727.jpg",
   "Author": "sal",
   "PrepareTime": "20 m",
   "CookTime": "5 m",
   "Ingredients": "tortillas,cheddar,monterey jack,cheddar,tomato,bell pepper,green onion,bean,salsa,chili",
   "Directions": "Preheat oven to 425 degrees F (220 degrees C). Lightly grease two 12 cup muffin pans.**Cut each tortilla into 6 smaller round pieces. Insert the pieces into the muffin tin cups. Arrange the white Cheddar cheese, Monterey Jack cheese, Cheddar cheese, tomato, red bell pepper, green onions, black beans, hot salsa and chili powder in the cups as desired.**Bake in the preheated oven 5 minutes, or until the cheeses are lightly browned and bubbly.**",
   "recipe_id": 22304
 },
 {
   "name": "Artichoke Spread Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/6232.jpg",
   "Author": "SARAHSUE",
   "PrepareTime": "15 m",
   "CookTime": "15 m",
   "Ingredients": "artichoke,cream cheese,parmesan,mayonnaise,garlic,dill",
   "Directions": "Preheat oven to 400 degrees F (200 degrees C).**Place the artichoke hearts in a food processor and process until smooth. Process the cream cheese, Parmesan cheese, mayonnaise, garlic and dill with the artichoke hearts until the mixture is smooth and well blended. Transfer to a 9 inch pie pan.**Bake in the preheated oven 10 to 15 minutes, or until bubbly and lightly brown.**",
   "recipe_id": 22305
 },
 {
   "name": "Cheese Wizards Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Donna",
   "PrepareTime": "5 m",
   "CookTime": "10 m",
   "Ingredients": "ground beef,cheese,pepper,cocktail",
   "Directions": "Preheat the broiler.**Place ground beef in a large, deep skillet. Cook over medium high heat until evenly brown. Drain and crumble.**In a medium bowl, mix together the beef, processed cheese sauce, salt and pepper. Spread the mixture  on the slices of cocktail rye.**Place the slices on a large baking sheet, and broil 5 minutes, or until the cheese sauce is melted.**",
   "recipe_id": 22307
 },
 {
   "name": "Fried Plantains Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/808222.jpg",
   "Author": "Donna",
   "PrepareTime": "5 m",
   "CookTime": "10 m",
   "Ingredients": "fry,plantain",
   "Directions": "Preheat oil in a large, deep skillet over medium high heat.**Peel the plantains and cut them in half. Slice the halves lengthwise into thin pieces.**Fry the pieces until browned and tender. Drain excess oil on paper towels.**",
   "recipe_id": 22308
 },
 {
   "name": "Creamy Lemon Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/218868.jpg",
   "Author": "LTIGGR2",
   "PrepareTime": "15 m",
   "CookTime": "35 m",
   "Ingredients": "lemon,lemon,water,topping thawed,lemon,vanilla,milk",
   "Directions": "Prepare and bake cake mix according to package directions for a 9x13 inch pan. Poke holes in cake while still hot with the round handle of a wooden spoon. Make gelatin with only 1 cup of boiling water. Pour liquid gelatin over cake while hot. Cool cake completely.**Beat together whipped topping, pudding mix, milk and vanilla extract.  Pour mixture over cooled cake and refrigerate until ready to serve.**",
   "recipe_id": 22310
 },
 {
   "name": "Lemon Raspberry White Chocolate Mousse Cake Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/3208575.jpg",
   "Author": "Paulette Womer",
   "PrepareTime": "30 m",
   "CookTime": "45 m",
   "Ingredients": "lemon,raspberry,cornstarch,chocolate,cream,vanilla,raspberry",
   "Directions": "Prepare and bake cake mix according to package directions for two 9 inch round pans. Cool cakes completely, then split each in half to make 4 layers.**To make Raspberry Filling:  In a blender or food processor, puree raspberries. In a saucepan, heat pureed raspberries until boiling. Mix cornstarch with a small amount of water and stir into raspberries. cook, stirring constantly, for 5 minutes, or until thickened. Set aside to cool.**To make White Chocolate Mousse:  In the top of a double boiler, heat white chocolate with 1 cup of the cream, stirring occasionally, until chocolate is melted and smooth. Remove from heat and allow to cool to lukewarm. Whip the remaining 2 cups cream until soft peaks form. Stir in the vanilla. Fold 1/3 of the whipped cream into the white chocolate mixture, then quickly fold in the remaining whipped cream. Do not over-mix, or the mousse will become grainy.**Place 1 cake layer on serving plate and spread with white chocolate mousse. Place the next layer on top and spread with raspberry filling. Repeat next layer of cake with mousse. Cover with the final layer of cake. Frost top and sides with mousse. Pipe a border with remaining mousse. Garnish with fresh berries.**",
   "recipe_id": 22312
 },
 {
   "name": "Fat Free Refried Beans Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/5366079.jpg",
   "Author": "BROMFIELD",
   "PrepareTime": "10 m",
   "CookTime": "15 m",
   "Ingredients": "bean,water,garlic,pepper,salt,tea,onion",
   "Directions": "In a small bowl mash 2/3 cup of beans to a smooth paste.**In a medium saucepan over medium heat, combine the remaining  beans with the water.  When heated through, stir in garlic, pepper, salt and liquid smoke.**Stir the bean paste into the whole beans and mix well.  Stir in the onion and cook for 10 minutes, or until onions are slightly cooked.**",
   "recipe_id": 22314
 },
 {
   "name": "Corn and Zucchini Melody Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/454410.jpg",
   "Author": "MOLSON7",
   "PrepareTime": "5 m",
   "CookTime": "25 m",
   "Ingredients": "bacon,zucchini,corn,onion,pepper,monterey jack",
   "Directions": "Place bacon in a large, deep skillet. Cook over medium-high heat until evenly brown. Reserve 1 tablespoon of drippings. Drain bacon, chop, and set aside.**Heat the bacon drippings in the skillet over medium heat. Saute the zucchini, corn, and onion until tender but still crisp, about 10 minutes. Season with pepper. Spoon vegetables into a bowl, and sprinkle with chopped bacon and  shredded cheese.**",
   "recipe_id": 22315
 },
 {
   "name": "'Christian''s Crazy Sherpa Potatoes Recipe '",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/860674.jpg",
   "Author": "Barb",
   "PrepareTime": "15 m",
   "CookTime": "15 m",
   "Ingredients": "butter,garlic,potato,pea,broccoli,carrot,zucchini,bell pepper,cheddar",
   "Directions": "Melt butter over medium heat and saute garlic.  Stir in potato, peas, broccoli, carrot, zucchini and bell pepper.  Stirring occasionally, cook until potatoes start to brown, about 15 minutes.  Serve with shredded cheese.**",
   "recipe_id": 22316
 },
 {
   "name": "Gooey Cherry Bars Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/6559.jpg",
   "Author": "Ruthie Isaacs",
   "PrepareTime": "20 m",
   "CookTime": "40 m",
   "Ingredients": "flour,white sugar,butter,egg,brown sugar,vanilla,baking powder,cherry,walnut,sugar,butter",
   "Directions": "'Preheat oven to 350 degrees F (175 degrees C).  Lightly grease a 9x13 inch baking dish.**In a medium bowl, mix flour, white sugar and 3/4 cup butter until crumbly.  Press into prepared pan.**Bake in preheated oven 12 to 15 minutes, until light brown.**In a food processor, combine eggs, brown sugar, vanilla and baking powder and process until smooth.  Pour in cherries and walnuts and pulse until just chopped and incorporated, but not pulverized.  Pour over crust.**Bake 25 minutes, until center is set.**To frost, cream together confectioners'' sugar with 2 tablespoons butter and 4 tablespoons cherry juice until fluffy.  Frost cooled dessert and cut into bars.**'",
   "recipe_id": 22320
 },
 {
   "name": "'DT''s Beef Dip Recipe '",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1082245.jpg",
   "Author": "DT Marquardt",
   "PrepareTime": "10 m",
   "CookTime": "X",
   "Ingredients": "cream cheese,green onion,beef,milk,2 tablespoons Beau Monde  seasoning",
   "Directions": "In a medium bowl, beat cream cheese until smooth.  Stir in onion and beef.  Beat in milk, a little at a time, until dip is the consistency of a thick pea soup.  Stir in seasoning.  Refrigerate 8 hours or overnight before serving.**",
   "recipe_id": 22321
 },
 {
   "name": "Slow Cooker Chicken Dressing Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/269708.jpg",
   "Author": "Mindy McCoy",
   "PrepareTime": "30 m",
   "CookTime": "4 h 30 m",
   "Ingredients": "chicken,bread,bread,egg,onion,salt,black pepper,sage,chicken broth,chicken,margarine",
   "Directions": "Place chicken in a pot with water to cover, and bring to a boil over medium heat. Boil 20 minutes, or until cooked through.  Cool, and cut into pieces.**In a slow cooker, stir together chicken, cornbread, bread, eggs, onion, salt, pepper, sage, chicken broth, and chicken soup. Stir until well blended. Dot with margarine.**Cover, and cook on Low for 3 to 4 hours. Remove lid, and fluff with fork. Let rest 15 minutes before serving.**",
   "recipe_id": 22322
 },
 {
   "name": "Cream Cheese Candies Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/206715.jpg",
   "Author": "Jackie Smith",
   "PrepareTime": "20 m",
   "CookTime": "X",
   "Ingredients": "cream cheese,pepper,sugar",
   "Directions": "'In a small mixing bowl, beat cream cheese with peppermint extract.  Beat in half the confectioners'' sugar until smooth.  Knead in remaining confectioners'' sugar until fully incorporated.  Shape dough into 1/2 inch balls, place on baking sheets, flatten with a fork, and allow to stand 1 hour to harden.  Store in airtight containers in refrigerator.**'",
   "recipe_id": 22323
 },
 {
   "name": "Almond Chocolate Coconut Cups Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/643868.jpg",
   "Author": "ZIPITY",
   "PrepareTime": "45 m",
   "CookTime": "10 m",
   "Ingredients": "chocolate,egg,margarine,flour,white sugar,milk,marshmallow,coconut,milk,chocolate,margarine,almond",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).  Grease mini-muffin tins.**In a bowl, combine cake mix, egg, 1/2 cup melted margarine and flour until well blended.  Roll into 1 inch balls and place in prepared mini-muffin pans.  Press into bottom and up sides of muffin cups.**Bake in preheated oven 10 minutes, until set.**While cups are baking, combine 1/2 cup sugar and 1/2 cup evaporated milk in microwave-safe bowl.  Microwave on high 2 minutes, until mixture comes to a boil.  Stir in marshmallows until melted.  Stir in coconut until well combined.  Spoon into baked shells while mixture is still warm.**In a microwave-safe bowl, combine 1/4 cup evaporated milk, chocolate chips and 2 tablespoons margarine.  Microwave on high 1 minute, remove from oven and stir until chocolate is melted and mixture is smooth.  Stir in almonds until well coated.  Spoon over coconut mixture and spread to cover.  Cool completely before removing from pans.  Store in refrigerator or freezer.**",
   "recipe_id": 22328
 },
 {
   "name": "Pork Chop and Potato Casserole Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/586338.jpg",
   "Author": "Valkyrja",
   "PrepareTime": "20 m",
   "CookTime": "45 m",
   "Ingredients": "pork chop,potato,mushroom",
   "Directions": "In a large skillet, brown pork chops with a little oil over medium-high heat.  An electric skillet can also be used.**Add potatoes and condensed soup.  Do not dilute soup.  Cover and cook for 45 minutes, or until potatoes and chops are fully cooked.**",
   "recipe_id": 22329
 },
 {
   "name": "Pecan Crackers Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/14004.jpg",
   "Author": "ANGIE V.",
   "PrepareTime": "10 m",
   "CookTime": "12 m",
   "Ingredients": "ham,pecan,white sugar,butter,margarine",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**Line a baking sheet with graham crackers.  Sprinkle evenly with pecans.**In a small saucepan over medium heat, combine sugar, butter and margarine.  Bring to a boil and boil 3 minutes.  Remove from heat and spoon mixture over pecans, coating well.**Bake in preheated oven 12 minutes, until golden.  Cool completely before serving.**",
   "recipe_id": 22330
 },
 {
   "name": "Barbequed Pineapple Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/5647610.jpg",
   "Author": "Michael Fischer",
   "PrepareTime": "15 m",
   "CookTime": "15 m",
   "Ingredients": "pineapple,rum,brown sugar,cinnamon,ginger,nutmeg,clove",
   "Directions": "Peel the pineapple and, leaving it whole, cut out the center core. Slice into 8 rings, and place them in a shallow glass dish or resealable plastic bag. In a small bowl, mix together the rum, brown sugar, cinnamon, ginger, nutmeg, and cloves. Pour marinade over the pineapple, cover, and refrigerate for 1 hour, or overnight.**Preheat grill for high heat. Lightly oil grate.**Grill pineapple rings 15 minutes, turning once, or until outside is dry and char marked. Serve with remaining marinade.**",
   "recipe_id": 22332
 },
 {
   "name": "Flan III Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/30160.jpg",
   "Author": "NMAR1KEN2",
   "PrepareTime": "15 m",
   "CookTime": "1 h",
   "Ingredients": "egg,egg,white sugar,cream,cream,vanilla,orange,liqueur",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**In a medium bowl, beat eggs and yolks.  Beat in sugar until smooth.  Set aside.**In a large saucepan over medium heat, combine cream, half-and-half, the vanilla bean and its scrapings, and the peel of one orange.  Heat until bubbles form at edges of liquid, reduce heat to low and simmer 15 minutes.  Beat hot cream into egg mixture, a little at a time, until all is incorporated.  Stir in orange liqueur.  Pour into 6 individual ramekins or custard cups.**Line a roasting pan with a damp kitchen towel.  Place ramekins on towel, inside roasting pan, and place roasting pan on oven rack.  Fill roasting pan with boiling water to reach halfway up the sides of the ramekins.**Bake in preheated oven 45 to 60 minutes, until set.  Let cool completely before serving.**",
   "recipe_id": 22334
 },{
   "name": "Never Fail Pie Crust III Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1709441.jpg",
   "Author": "PUDICAT",
   "PrepareTime": "10 m",
   "CookTime": "12 m",
   "Ingredients": "flour,shortening,flour,salt,water",
   "Directions": "In a large bowl, Cut the shortening into the 2 1/2 cups flour until the mixture resembles coarse crumbs.**In a small bowl, combine the 6 tablespoons flour, 2 teaspoons salt and 1/2 cup water to make a paste. Mix paste into the flour and shortening mixture.**Divide dough into 4 equal pieces and shape into rounds. Wrap securely in plastic and refrigerate overnight.**",
   "recipe_id": 22354
 },
 {
   "name": "Fruity Rice Delight Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Debi",
   "PrepareTime": "15 m",
   "CookTime": "20 m",
   "Ingredients": "water,rice,cocktail,topping thawed",
   "Directions": "In a medium saucepan bring water to a boil. Add rice and stir. Reduce heat, cover and simmer for 20 minutes.**In a medium bowl, blend 1/2 the fruit cocktail and the whipped cream. Drain any remaining fluid from the rice and mix 1/2 into the bowl. Continue mixing in the remaining fruit cocktail and rice until the desired consistency has been attained.**",
   "recipe_id": 22360
 },
 {
   "name": "Angry Dan Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/235516.jpg",
   "Author": "Dan",
   "PrepareTime": "1 m",
   "CookTime": "X",
   "Ingredients": "2 fluid ounces Southern Comfort,cinnamon,cola",
   "Directions": "In a glass full of ice, pour Southern Comfort and cinnamon schnapps. Fill glass with Cola.**",
   "recipe_id": 22361
 },
 {
   "name": "Thanksgiving Day Salad Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/276312.jpg",
   "Author": "HELLIPORT",
   "PrepareTime": "15 m",
   "CookTime": "X",
   "Ingredients": "water,strawberry,strawberry,cranberry sauce,pecan,lettuce,cream cheese,sour cream,white sugar,lemon juice",
   "Directions": "Boil the water and combine with the strawberry flavored gelatin mix in a medium bowl. Mix in the strawberries, cranberry sauce and pecans. Transfer to a 2 quart mold. Chill in the refrigerator 6 to 8 hours, or overnight.**Place the molded gelatin mixture on a serving plate and surround the base with lettuce leaves.**In a medium bowl, mix the cream cheese, sour cream, sugar and lemon juice with an electric mixer until well blended. Use this mixture as a topping for each serving of salad.**",
   "recipe_id": 22370
 },
 {
   "name": "Apple and Pecan Stuffing Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/783252.jpg",
   "Author": "Kathleen Burton",
   "PrepareTime": "15 m",
   "CookTime": "35 m",
   "Ingredients": "bread,pecan,apple",
   "Directions": "Prepare stuffing mix according to package directions.**Preheat oven to 325 degrees F (165 degrees C).**Mix pecans and apples into the stuffing.**Bake uncovered in the preheated oven 35 minutes, or until lightly browned.**",
   "recipe_id": 22373
 },
 {
   "name": "Italian Roast Beef I Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/855340.jpg",
   "Author": "MICHELLEM66",
   "PrepareTime": "15 m",
   "CookTime": "3 h 30 m",
   "Ingredients": "water,beef,salt,garlic,italian seasoning,black pepper,oregano,basil,red pepper,roast,vegetable oil",
   "Directions": "Pour water into a large kettle, and add bouillon cubes.**Mix together the salt, garlic, Italian seasoning, black pepper, oregano, basil, and red pepper flakes on a large plate. Rub roast with 1/2 cup vegetable oil. Roll roast in seasoning mixture until well coated. Place the roast in the kettle along with any left over seasoning mixture and oil.**Bring water to a boil, reduce heat, and simmer approximately  3 1/2 hours. Meat should  be tender and well done.**",
   "recipe_id": 22376
 },
 {
   "name": "Apple Cake VII Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/71488.jpg",
   "Author": "jillybeans",
   "PrepareTime": "30 m",
   "CookTime": "1 h",
   "Ingredients": "flour,baking soda,salt,cinnamon,butter,white sugar,brown sugar,egg,vanilla,apple",
   "Directions": "'Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 10 inch Bundt pan. Sift together the flour, baking soda, salt and cinnamon. Set aside.**In a large bowl, cream together the butter, brown sugar and white sugar until fluffy.  Beat in the eggs, one at a time, then stir in the vanilla. Beat in the flour mixture.  Fold in the shredded apples.**Pour batter into prepared pan. Bake in the preheated oven for 60 minutes, or until a toothpick inserted into the center of the cake comes out clean. Allow cake to cool in the pan for 60 minutes, then turn out and sprinkle with confectioners'' sugar, if desired.**'",
   "recipe_id": 22378
 },
 {
   "name": "Pumpkin Chiffon Pie Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1999892.jpg",
   "Author": "Carla  A. Lightsey, Houston, Texas",
   "PrepareTime": "30 m",
   "CookTime": "20 m",
   "Ingredients": "gelatin,water,egg,white sugar,pumpkin,milk,salt,cinnamon,spice,nutmeg,ginger,pastry",
   "Directions": "Mix the gelatin and water in a small bowl, and set aside.**In a medium bowl, beat the egg yolks until thick. Mix in 3/4 cup sugar, pumpkin, evaporated milk, salt, cinnamon, allspice, nutmeg and ginger.**In a double broiler, cook the mixture over boiling water, stirring constantly, until thick. Mix in the gelatin. Stir to dissolve. Remove from heat and allow the mixture to thicken until it mounds when dropped by the spoonful.**In a clean, dry medium bowl, beat the egg whites until soft peaks form. Gradually mix in the remaining 1/2 cup sugar, and continue beating until firm. Fold in the pumpkin mixture. Transfer to the pie crust. Chill until firm, about 1 hour.**",
   "recipe_id": 22379
 },
 {
   "name": "Pumpkin Torte I Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "BETHRECIPES",
   "PrepareTime": "40 m",
   "CookTime": "20 m",
   "Ingredients": "ham,butter,egg,brown sugar,cream cheese,pumpkin,white sugar,cinnamon,salt,egg,milk,gelatin,water,egg,white sugar",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**In a medium bowl, mix the graham crackers and butter. Press into the bottom of a 9x13 inch baking pan.**In a medium bowl, mix eggs and brown sugar. Blend in the cream cheese. Spoon the mixture over the layer of graham crackers.**Bake in the preheated oven 20 minutes. Remove from oven and allow to cool.**In a medium saucepan over medium heat, mix together pumpkin, sugar, cinnamon, salt, egg yolks and milk. Bring to a boil. Stir constantly until slightly thickened, about 1 minute. Remove from heat.**Mix the gelatin and water in a small bowl. Stir into the pumpkin mixture. Cool to room temperature.**In a small bowl, beat the egg whites and sugar until stiff. Fold into the pumpkin mixture. Spoon in a layer over the cream cheese mixture. Chill in the refrigerator 6 to 8 hours, or overnight.**",
   "recipe_id": 22380
 },
 {
   "name": "Beef Loaf Deluxe Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/275133.jpg",
   "Author": "SHIVERDEN",
   "PrepareTime": "15 m",
   "CookTime": "50 m",
   "Ingredients": "vegetable oil,potato,bell pepper,bell pepper,onion,egg,ground beef,parsley,worcestershire sauce,garlic,bread,zucchini,tomato sauce,pepper",
   "Directions": "Preheat oven to 400 degrees F (200 degrees C). Grease a 15x10 inch roasting pan. Place the potatoes, green and red peppers, and onions in the pan and toss with the 2 tablespoons of vegetable oil. Bake in a preheated oven, uncovered, for 20 minutes.**Meanwhile, in a mixing bowl, combine egg, ground beef, parsley, Worcestershire sauce, garlic and bread crumbs. Mix thoroughly. Shape into a loaf about 8x4x4 inches.**When vegetables have cooked for 20 minutes, reduce heat to 350 degrees F (175 degrees C). Take roasting pan out of oven and stir in zucchini. Push the vegetables to the sides of the pan. Place the meat loaf in the center of the pan and pour the tomato sauce over the loaf and vegetables. Season with salt and pepper to taste.**Bake in a preheated oven, uncovered, for 30 minutes or until done.**",
   "recipe_id": 22383
 },
 {
   "name": "Tex",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/755784.jpg",
   "Author": "ANNMILLER",
   "PrepareTime": "30 m",
   "CookTime": "15 m",
   "Ingredients": "flour,brown sugar,baking soda,cinnamon,salt,margarine,water,cocoa powder,coffee,milk,egg,vanilla,margarine,cocoa powder,coffee,milk,sugar,almond",
   "Directions": "'Preheat oven to 350 degrees F (175 degrees C). Grease and flour an 10x15 inch jelly roll pan.  Combine the flour, baking soda, brown sugar, cinnamon and salt. Set aside.**In a small saucepan, melt 1 cup margarine.  Stir in water, 1/4 cup cocoa and 1 tablespoon instant coffee.  Bring mixture to a boil, then remove from heat.**Make a well in the center of the dry ingredients.  Pour in the cocoa mixture, then stir in 1/3 cup sweetened condensed milk, eggs and vanilla.  Mix until blended.**Pour batter into prepared pan. Bake in the preheated oven for 15 to 20 minutes, or until the cake springs back when lightly touched. Allow to cool.**For the coffee glaze:  In a small saucepan, melt 1/4 cup margarine.  Mix in 1/4 cup cocoa, 1 tablespoon instant coffee and  sweetened condensed milk, and confectioners'' sugar.  Stir until blended.  Fold in the almonds.  Spread glaze over warm cake.**'",
   "recipe_id": 22388
 },
 {
   "name": "Special Deviled Eggs Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/4526971.jpg",
   "Author": "Sara",
   "PrepareTime": "10 m",
   "CookTime": "12 m",
   "Ingredients": "egg,mayonnaise,onion,pickles,horseradish,mustard,paprika,pepper",
   "Directions": "Place eggs in a medium saucepan and cover with cold water. Bring water to a boil and immediately remove from heat. Cover and let eggs stand in hot water for 10 to 12 minutes. Remove from hot water, cool, peel and cut lengthwise.**Remove yolks from eggs. In a medium bowl, mash the yolks and mix together with mayonnaise, onion, sweet pickle relish, horseradish and mustard.**With a fork or pastry bag, fill the egg halves with the yolk mixture. Garnish with paprika, salt and pepper. Chill until serving.**",
   "recipe_id": 22390
 },
 {
   "name": "Black Russian Cake II Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "sal",
   "PrepareTime": "20 m",
   "CookTime": "45 m",
   "Ingredients": "cake,water,vegetable oil,chocolate,cinnamon,clove,coffee,egg,chocolate,liqueur,vodka",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C). Grease and flour a 10 inch Bundt pan.**Beat together the cake mix, water, vegetable oil, instant pudding mix, cinnamon, cloves, instant coffee and eggs until blended.  Pour into prepared pan and bake for 45 minutes, or until a toothpick inserted in the center comes out clean.  Cool before frosting.**For the frosting:  Mix together the frosting, coffee liqueur and vodka until blended.  Spread onto cooled cake.**",
   "recipe_id": 22393
 },
 {
   "name": "Sausage Smothered in Red Cabbage Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/13919.jpg",
   "Author": "Karen Long",
   "PrepareTime": "30 m",
   "CookTime": "30 m",
   "Ingredients": "cabbage,apple,salt,lemon juice,water,butter,onion,black pepper,vinegar,sausage",
   "Directions": "Place the cabbage in a large kettle, and add the diced apple, 2 teaspoons of the salt, lemon juice, and 1/2 cup water. Bring to a boil then simmer, covered, about 15 minutes stirring occasionally.**In hot butter, saute the onion until golden.  Add the onion to the cabbage along with 1 teaspoon salt, pepper, vinegar and sausage. Cook, covered, 20 to 30 minutes until sausage is heated through.  To serve, spoon the cabbage onto a heated platter, topping it with the sausage.**",
   "recipe_id": 22397
 },
 {
   "name": "Chili con Carne II Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/502331.jpg",
   "Author": "BUBBLE",
   "PrepareTime": "20 m",
   "CookTime": "45 m",
   "Ingredients": "vegetable oil,onion,chile pepper,garlic,ground beef,tomato,salt,black pepper,cumin,chili,paprika,oregano,cinnamon,clove,bean",
   "Directions": "In a medium sized stock pot, heat the oil over medium heat. Saute onion, chile pepper and garlic until soft. Add ground beef: cook and stir until meat is browned.**Pour in tomatoes with liquid, salt, pepper, cumin, chili powder, paprika, oregano, cinnamon sticks, and cloves. Cover and simmer for 45 minutes.**Stir in kidney beans, and cook another 15 minutes. Remove cinnamon sticks before serving.**",
   "recipe_id": 22403
 },
 {
   "name": "Pork Chop Casserole III Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/374834.jpg",
   "Author": "FRZZLD_1",
   "PrepareTime": "10 m",
   "CookTime": "1 h",
   "Ingredients": "rice,onion,mushroom,water,bell pepper,onion,pork chop",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**Spread rice in the bottom of a 9x13 inch baking dish. Sprinkle contents of dried onion soup mix over rice. Mix mushroom soup with water, and pour over rice. Arrange the bell pepper and onion slices over soup and rice mixture. Place pork chops on top of pepper and onions. Cover the dish with a lid or aluminum foil.**Bake for 1 hour in the preheated oven, until pork chops are very tender, and rice is fully cooked.**",
   "recipe_id": 22417
 },
 {
   "name": "Philly Mashed Potatoes Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/6005502.jpg",
   "Author": "Kimber",
   "PrepareTime": "5 m",
   "CookTime": "50 m",
   "Ingredients": "potato,cream cheese,onion,egg,flour,salt,pepper,onion",
   "Directions": "Preheat oven to 300 degrees F (150 degrees C).**Bring a large pot of salted water to a boil.  Add potatoes and cook until tender but still firm, about 15 minutes. Drain and mash.**In a large mixing bowl combine mashed potatoes, cream cheese, onion, eggs, flour, salt and pepper. Using an electric mixer, beat on medium speed for several minutes.  Spoon mixture into a 1 1/2 quart casserole dish and top with crushed fried onions.**Bake in preheated oven for 30 to 35 minutes.**",
   "recipe_id": 22420
 },
 {
   "name": "Pork Chops and Scalloped Potatoes Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/1056539.jpg",
   "Author": "JAMON0126",
   "PrepareTime": "30 m",
   "CookTime": "1 h 30 m",
   "Ingredients": "butter,salt,black pepper,flour,chicken broth,pork chop,potato,paprika",
   "Directions": "Preheat oven to 350 degrees F (175 degrees C).**In sauce pan melt 1 tablespoon butter over medium heat.  Add salt, pepper and flour.  Pour in the chicken broth, cook and stir until mixture boils. Remove from heat and set aside.**In skillet brown pork chops in 1 tablespoon butter.  Grease a cooking dish with the remaining tablespoon butter and layer potatoes.  Pour mixture over potatoes and place browned chops on top. Sprinkle paprika on top.**Cover and bake for 1 hour.  Uncover and bake for an additional 30 minutes.**",
   "recipe_id": 22422
 },
 {
   "name": "Crawfish Etouffee III Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "Stacy Taylor",
   "PrepareTime": "10 m",
   "CookTime": "40 m",
   "Ingredients": "onion,tomato,mushroom,chile pepper,fish",
   "Directions": "In a large saucepan on medium heat, saute onion until clear. Add tomato soup, mushroom soup, and canned tomatoes. Simmer for 15 minutes.**Place the crawfish into the pan and simmer for 25 minutes.**",
   "recipe_id": 22427
 },
 {
   "name": "Corn Pudding Custard Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/250x250/666865.jpg",
   "Author": "sal",
   "PrepareTime": "5 m",
   "CookTime": "20 m",
   "Ingredients": "cream,salt,pepper,butter,egg,white sugar,corn",
   "Directions": "Combine the cream with salt and pepper in a small saucepan and heat until it bubbles.  Stir in butter, eggs, sugar and corn.  Transfer to a microwave safe dish.**Microwave on high for 20 minutes.  Let stand 10 minutes to thicken.**",
   "recipe_id": 22432
 },
 {
   "name": "Cheese and Nut Log Recipe ",
   "Photo": "https://images.media-allrecipes.com/images/79591.png",
   "Author": "MS.CHEF",
   "PrepareTime": "30 m",
   "CookTime": "X",
   "Ingredients": "cheddar,cream cheese,green onion,bell pepper,garlic,worcestershire sauce,blue cheese,milk,pistachio",
   "Directions": "In a small bowl, mix the Cheddar cheese and 1/2 the cream cheese with an electric mixer until well blended. Mix in the green onions, red bell peppers, garlic and Worcestershire sauce. Chill in the refrigerator 30 minutes.**In a small bowl, mix the blue cheese, milk and remaining cream cheese with the electric mixer until well blended.**Shape the chilled Cheddar cheese mixture into an 8 inch log. Spread the blue cheese mixture evenly over the top and sides of the log. Cover with pistachio nuts. Chill in the refrigerator 2 to 3 hours before serving.**",
   "recipe_id": 22437
 },
 {
   "name": "Deviled Eggless Salad Recipe ",
   "Photo": "https://images.media-allrecipes.com/userphotos/560x315/484348.jpg",
   "Author": "SPK",
   "PrepareTime": "15 m",
   "CookTime": "X",
   "Ingredients": "cottage cheese,mayonnaise,low fat,mustard,soy sauce,tea,worcestershire sauce,vinegar,tofu,green onion",
   "Directions": "In a food processor or blender combine cottage cheese, mayonnaise, yogurt, mustard, soy sauce, turmeric, Worcestershire sauce and vinegar.  Process until well blended.  Add tofu and pulse a few times, maintaining a bit of texture.  Stir in green onions.  Refrigerate for at least 3 hours to allow flavors to meld.**",
   "recipe_id": 22445
 },
      ],
      searchRecipe: '',
      searchIngr: '',
      searchTime: '',
      all: true,
      range: ''
      // name: ''
    }
  },

  
  computed: {

    filteredData: function(){
      return this.data 
      .filter((recipe) => {
        return recipe.name.toLowerCase().match(this.searchRecipe.toLowerCase())
      })
      .filter((recipe) => {
        return recipe.Ingredients.toLowerCase().match(this.searchIngr.toLowerCase())
      })
    }
    
  }
}
</script>
