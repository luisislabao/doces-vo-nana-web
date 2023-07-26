<template>
    <section id="section">   
        <h1>{{this.category}}</h1>
        <div v-for="product in productstoshow" :key="product.id">
        <p>{{product.name}}</p>
        </div>
    </section>
</template>
<script>
import {newProducts} from './get-products.vue';
// import Swal from "sweetalert2";
export default {
    nome: 'Board_Itens',
    props: {
        category: String
    },
    data() {
        return {
            productstoshow: [],
            teste:newProducts,
        }
    },  
    methods: {
        getproductsByCategory(){   
            console.log(this.category)
            this.teste = this.teste.map((produto) => {
                produto.categories.map((category) => {
                    if(category.name == this.category){
                       this.productstoshow.push(produto)
                    }
                })           
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
h1{
    color: beige;
}
div{
    justify-content: space-between;
    border-radius: 20px;
    padding: 2px;
    margin: 10px;
    width: 20%;
    min-height: 100px;
    background-color: aquamarine;
}


</style>
