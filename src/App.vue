<template>
  <section id="sec">
    <HelloWorld></HelloWorld>
    <carousel :items-to-show="1">
      <slide v-for="slide in 8" :key="slide">
        <carousel__item v-if="(slide == 1)"> <img src="../src/assets/carrouseltest/1.png"> </carousel__item>
        <carousel__item v-if="(slide == 2)"> <img src="../src/assets/carrouseltest/2.png"> </carousel__item>
        <carousel__item v-if="(slide == 3)"> <img src="../src/assets/carrouseltest/3.png"> </carousel__item>
        <carousel__item v-if="(slide == 4)"> <img src="../src/assets/carrouseltest/4.png"> </carousel__item>
        <carousel__item v-if="(slide == 5)"> <img src="../src/assets/carrouseltest/5.png"> </carousel__item>
        <carousel__item v-if="(slide == 6)"> <img src="../src/assets/carrouseltest/6.png"> </carousel__item>
        <carousel__item v-if="(slide == 7)"> <img src="../src/assets/carrouseltest/7.png"> </carousel__item>
        <carousel__item v-if="(slide == 8)"> <img src="../src/assets/carrouseltest/8.png"> </carousel__item>
      </slide>
      <template #addons>
        <navigation />
        <pagination />
      </template>
    </carousel>
    <br>
    <div id="seeker">
      <input type="text" placeholder="Aqui você pesquisa teu docin!!🔎" id="pesquisa"><select name="categoria"
        id="tipos"></select>
    </div>
    <div v-if="ok == true">
      <div v-for="category in categories" :key="category.id">
        <!-- <pre>{{category}}</pre> -->
      <Board_Itens :category="category" ></Board_Itens>
    </div>
    </div>
  </section>  
</template>

<script>
import { newProducts } from "./components/get-products.vue";
import HelloWorld from "../src/components/header.vue";
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import { products } from "./components/get-products.vue";
import Board_Itens from "@/components/my_bording-itens.vue";
export default {
  name: 'App',
  components: {
    HelloWorld,
    Carousel,
    Slide,
    Pagination,
    Navigation,
    Board_Itens
  },
  data() {
    return {
      ok: false,
      newProducts,
      categories: []
      
    }
  },
  mounted() {
    let placeholder = document.createElement('option')
    placeholder.innerText = 'Ou navega nas categorias 🚣🏼‍♂️ '
    let select = document.getElementById('tipos')
    select.appendChild(placeholder)
    for (let tipo in products) {
      placeholder = document.createElement('option')
      placeholder.innerText = `${tipo}`
      let select = document.getElementById('tipos')
      select.appendChild(placeholder)
    }
    this.ok = true 
    this.newProducts = newProducts.map((products) => 
    {products.categories.map((category) => {
    if (this.categories.indexOf(category.name) < 0) {
    this.categories.push(category.name)
    }
      })} )

    }
  }

</script>

<style s>
#seeker {
  margin: 10px;
  padding: 10px;
  display: flex;
  justify-content: center;

}

#pesquisa {
  width: 200px;
  height: 25px;
  border-radius: 20px;
  box-shadow: #e69e9ee0 10px 10px 10px;
}

#tipos {
  width: 200px;
  height: 30px;
  border-radius: 20px;
  box-shadow: #e69e9ee0 10px 10px 10px;
}

body {
  padding: 0;
  margin: 0;
  text-align: center;
  background-color: bisque;
}

.carousel__item {
  min-height: 200px;
  width: 100%;
  background-color: var(--vc-clr-primary);
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid #e69e9ee0;
}

#section {
  background-color: #e99f9fe0;
  ;
  width: 90%;
  height: auto;
  margin-right: auto;
  margin-left: auto;
  padding: 10px;
  border-radius: 20px;
}

#val {
  background-image: url("assets/trabalhador-da-estrada.png");
  min-height: 150px;
  width: 25%;
  background-color: beige;
  border-radius: 20px;
  margin: 10px;
  text-align: center;
  display: inline-block;
  padding: 1px;
  
}

select {
  width: 100px;
  border-radius: 20px;
}</style>

