<template>
    <section id="section">
        <h1>{{ this.category }}</h1>
        <div class="productareawraper">
            <div class="productarea" v-for="product in productstoshow" :key="product.id">
                <img src="../assets/trabalhador-da-estrada.png" @click="Callfunc(product.name, product.Quantitie)">
                <p>{{ product.name }}</p>
            </div>
        </div>
    </section>
</template>
<script>
import Swal from 'sweetalert2';
import { newProducts } from './get-products.vue';
export default {
    nome: 'Board_Itens',
    props: {
        category: String
    },
    data() {
        return {
            productstoshow: [],
            newProducts
        }
    },
    methods: {
        getproductsByCategory() {
            console.log(this.category)
            this.newProducts = this.newProducts.map((produto) => {
                produto.categories.map((category) => {
                    if (category.name == this.category) {
                        this.productstoshow.push(produto)
                    }
                })
            })
        },
        Callfunc(x, y) {
            console.log(x, y)
            Swal.fire({
                title: 'Quantos?',
                text: 'Disponivel: ' + y,
                type: 'question',
                input: 'range',
                inputLabel: 'aaaa',
                inputAttributes: {
                    min: 1,
                    max: y,
                    step: 1
                },
                inputValue: 0,
                confirmButtonColor: '#e99f9fe0',
            })
        }
    },
    mounted() {
        // this.injection()
        this.getproductsByCategory()
    }
}
</script>

<style scoped> 

h1 {
     color: beige;
     font-size: xx-large;
 }

 .productarea {

     justify-content: space-between;
     border-radius: 20px;
     padding: 2px;
     margin: 10px;
     width: 20%;
     min-height: 100px;
     background-color: aqua;
 }

 .productareawraper {
     display: flex;
     flex-direction: row;
     flex-wrap: wrap;
     justify-content: center;
 }
</style>
