<template>
    <section id="section">
        <h1>{{ this.category }}</h1>
        <div class="productareawraper">
            <div class="productarea" v-for="product in productstoshow" :key="product.id">
                <img :id="product.name" src="../assets/trabalhador-da-estrada.png">
                <br><select :id="'Select' + product.name"><br>
                    <option :value="product.Quantitie">Max. {{ product.Quantitie }} Und.</option>
                    <option v-for="count in (product.Quantitie)" :key="count--">{{ count }} Unidades</option>
                </select>
                <button @click="emit(product.name, category)">Adicionar</button>
            </div>
        </div>
    </section>
</template>
<script>
let iten = []
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
        // emit(nm, tp) {
        //     let id = document.getElementById(`Select${nm}`)
        //     let message = `${id.value}`
        //     let obg = {und: `${message}`, nome: `${nm}`, type: `${tp}`}
        //     console.log(`Borading diz: ${obg}`)
        //     if (id.value != '0 Unidades') {
        //         this.$emit('tellto-Header', obg )
        //     }
        // },
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

<style scoped> select {
     width: 80%;
     height: 15%;
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
 }</style>
