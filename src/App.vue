<template>
  <div class='main'>
    <h1> Recipes </h1>
    <input type="text" placeholder="Enter the recipe's title" v-model='search'> 
    <div>
      <div class='recipes'>
      <div class='recipe__instance' v-for='d in filteredData' :key=d>
        <div >
          <h2>{{d.name}}</h2>
          <img class='recipe__photo' :src="d.Photo" alt="">
          <p class='recipe__ingredients'> <span>You will need:</span> {{d.Ingredients}}</p> 
          <div>
            <p><span>Prepare time:</span>  {{d.PrepareTime}}</p> 
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
import axios from 'axios'
import {mapState, mapMutations} from 'vuex'
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
      ],
      search: ''
    }
  },
  
  methods: {
    ...mapMutations(['FILTER_RECIPES']),
    filterRecipes(search){
      this.FILTER_RECIPES(search)
    },
    sayHi(){
      alert('hu')
    }
  },
  
  computed: {
    ...mapState({
      Recipes: state => state.Recipes,
      FilteredRecipes: state => state.filteredRecipes
    }),
    filteredData : function(){
        return this.data.filter((recipe) => {
          return recipe.name.match(this.search)
        })
      }
    
  }
}
</script>
