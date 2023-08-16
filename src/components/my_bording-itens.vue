<template>
    <section id="section">
        <h1>{{ this.category }}</h1>
        <div class="productareawraper">
            <div class="productarea" v-for="product in productstoshow" :key="product.id">
                <img :id="product.name" src="../assets/trabalhador-da-estrada.png">
                <p>{{ product.name }} - {{product.price}} R$ </p>
                <select :id="'Select' + product.name">
                    <option :value="product.Quantitie">Max. {{ product.Quantitie }} Und.</option>
                    <option v-for="count in (product.Quantitie)" :key="count--">{{ count }} Unidades</option>
                </select>
                <button @click="emit(product.name, product.price, category)">Adicionar</button>
            </div>
        </div>
    </section>
</template>
<script>
let iten = []
import axios from 'axios'
import { newProducts } from './get-products.vue';
export default {
    nome: 'Board_Itens',
    props: {
        category: String,
    },
    data() {
        return {
            productstoshow: [],
            newProducts,
            iten,
        }
    },
    methods: {
        // Lembrete, resolver isso via backend
        emit(nm, pr, tp) {
            let id = document.getElementById(`Select${nm}`)
            let message = `${id.value}`
            let obg = { 'name': `${nm}`, 'type': `${tp}`, 'price': `${pr}`, 'qnt': `${message}` }
            console.log('Board diz:')
            console.table(obg)
            let axiosConfig = {
                headers: {
                    'Content-Type': 'application/json',
                },
            };
            if (id.value != '0 Unidades') {
                axios.post(`http://localhost:5000/cesta/`, obg, axiosConfig)
                    .then(function (response) {
                        return `enviado! ${response}`
                    })
                    .catch(function (error) {
                        return error
                    })
            }
        }
        ,
        getproductsByCategory() {
            this.newProducts = this.newProducts.map((produto) => {
                produto.categories.map((category) => {
                    if (category.name == this.category) {
                        this.productstoshow.push(produto)
                    }
                })
            })
        },
    },
    mounted() {
        // this.injection()
        this.getproductsByCategory()
    }
}
</script>

<style scoped> 
p{
    font-family: cursive;
    color: rgb(216, 12, 12);
}

select {
     width: 80%;
     height: 10%;
     border-radius: 10px;
     color: brown;
 }

 h1 {
     color: rgb(201, 50, 50);
     font-size: xx-large;
     /* background-color: tomato; */
 }

 .productarea {
     justify-content: space-between;
     border-radius: 20px;
     padding: 2px;
     margin: 10px;
     width: 20%;
     min-height: 100px;
     background-color: aqua;
     text-align: center;
 }

 img:hover {
     cursor: pointer;
 }

 .productareawraper {
     display: flex;
     flex-direction: row;
     flex-wrap: wrap;
     justify-content: center;
 }

 button {
     border-radius: 20px;
     background-color: bisque;
     color: brown;
 }

 button:hover {
     cursor: pointer;
 }
</style>
