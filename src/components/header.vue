<template>
    <div class="container">
        <img @click="menu()" @mouseenter="colorin('menu')" @mouseleave="colorout('menu')" id="menu"
            src="../assets/icons8-cardápio-512.png">

        <div>
            <img class="headerbuttom" src="../assets/instagram.png"
                @click="insta('https://www.instagram.com/bolosdavonana/')" @mouseenter="colorin('logo')"
                @mouseleave="colorout('logo')" id="logo">
            <p> Bolos da Vó Nana</p>
        </div>
        
        <img @click="cesta()" @mouseenter="colorin('cesta')" @mouseleave="colorout('cesta')" id="cesta"
            src="../assets/cesta-64.png">
        
            <button class="shopButton" @click="pedido()" type="button">Fazer pedido!!</button>

        <!-- menu flutuante -->
        <div @mouseleave="close()" id="myDropdown" class="dropdown-content">
            <a href="http://localhost:5000/products/" target="_blank">Funcionário</a><br>
            <hr>
            <a href="#about">Sobre nós</a><br>
            <hr>
            <a href="https://api.whatsapp.com/send?phone=5553991755953&text=Olá!%20Gostaria%20de%20saber%20mais%20sobre%20seus%20produtos."
                target="_blank">Contate-nos</a><br>
            <hr>
        </div>

    </div>
</template>
<script>
import Swal from 'sweetalert2';
import { products } from '@/components/get-products.vue'

export default {
    name: "HelloWorld",
    methods: {
        colorin(x) {
            document.getElementById(x).style.backgroundColor = "#ffe4c4";
            document.getElementById(x).style.color = "#e99f9fe0"
        },
        colorout(x) {
            if (x == 'input') {
                document.getElementById(x).style.backgroundColor = "#FFF";
            }
            else if (x == 'logo') {
                document.getElementById(x).style.color = "#FFF";
                document.getElementById(x).style.backgroundColor = "#e99f9fe0";
            }
            else { document.getElementById(x).style.backgroundColor = "#e99f9fe0"; }

        },
        insta(x) {
            window.open(x)
        },
        cesta() {
            console.log(products)
            let block = ''
            let cesta = ''

            for (let propriedade in products) {
                for (let produto in products[propriedade]) {

                    block = `[${products[propriedade][produto].quantidade}.itens]-${products[propriedade][produto].nome}\n`
                    cesta += block.padEnd(40, '-');
                }
            }
            console.log(cesta)
            Swal.fire({
                title: '🌟 SUA CESTA 🌟 \n🙂',
                text: `\n${cesta}`,
                confirmButtonColor: '#e99f9fe0',
                width: 400,
                padding: '3em',


            })
        },
        menu() {
            document.getElementById("myDropdown").classList.toggle("show");
        },
        pedido() {
            Swal.fire({
                position: 'top-end',
                type: 'success',
                text: 'Pedido enviado para o email {placeholder}@gmail.com, favor aguardar resposta...',
                showConfirmButton: false,
                background: '#ffe4c4',
                timer: 3500
            })
        },
        close() {
            document.getElementById("myDropdown").classList.remove("show");
        }
    }
}
</script>
<style scoped>
p {
    color: #ffe4c4;
    font-family: cursive;
    font-size: x-large;
}

div {
    display: flex;
}

.container {
    display: flex;
    background-color: #e69e9ee0;
    justify-content: space-around;
    width: 100%;
    height: 60px;
}

img {
    max-width: 400px;
    max-height: 60px;
    background-color: #e99f9fe0;
    ;
}

.shopButton {
    border-radius: 20px;
    width: 130px;
    background-color: rgb(255, 255, 255);
    color: rgba(233, 159, 159, 0.88);
    height: 50px;
    margin-block: auto;
    border: none;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.shopButton:hover {
    background-color: bisque;
}

.shopButton:active {
    background-color: aquamarine;
}

/* aqui é o teste de menu */
.dropdown-content {
    font-family: cursive;
    display: none;
    position: absolute;
    background-color: #e99f9fe0;
    min-width: 260px;
    overflow: auto;
    border-radius: 20px;
    box-shadow: 10px 18px 16px 10px rgba(0, 0, 0, 0.2);
    z-index: 1;
}

.dropdown-content a {
    color: bisque;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
}

.show {
    display: block;
}

/* <!-- seetalert style --> */</style> 