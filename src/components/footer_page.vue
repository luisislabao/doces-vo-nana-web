<template>
    <div class="container">
        <!-- <div>
            <img class="headerbuttom" src="../assets/instagram.png"
                @click="insta('https://www.instagram.com/bolosdavonana/')" @mouseenter="colorin('logo')"
                @mouseleave="colorout('logo')" id="logo">
            <p> Bolos da Vó Nana</p>
        </div>

        <img @click="cesta()" @mouseenter="colorin('cesta')" @mouseleave="colorout('cesta')" id="cesta"
            src="../assets/cesta-64.png">

        <button class="shopButton" @click="pedido()" type="button">Fazer pedido!!</button>

        menu flutuante
        <div @mouseleave="close()" id="myDropdown" class="dropdown-content">
            <p
                @click="autority()">Funcionário</p><br>
            <hr>
            <a href="#about">Sobre nós</a><br>
            <hr>
            <a href="https://api.whatsapp.com/send?phone=5553991755953&text=Olá!%20Gostaria%20de%20saber%20mais%20sobre%20seus%20produtos."
                target="_blank">Contate-nos</a><br>
            <hr>
        </div> -->
        <ul>
            <li>Endereço: <a href="https://goo.gl/maps/tsVERDbMcniT8AH5A" target="_blank">Rua 16 n°269</a></li>
            <li>whatsapp: <a href="https://api.whatsapp.com/send?phone=5553991755953&text=Olá!%20Gostaria%20de%20saber%20mais%20sobre%20seus%20produtos." target="_blank">-55-(53) 9 9175-5953</a></li>
        </ul>
        <img src="../assets/imagem_150x150.jpg">
        <ul>
            <li>Instagram: <a href='https://www.instagram.com/bolosdavonana/' target="_blank">Bolos Da Vó Naná</a></li>
            <li>Sobre-nós: <a href="https://media.tenor.com/P4DqOBNDfT4AAAAd/give-me-give-it-to-me.gif" target="_blank">MAMACO</a></li>
        </ul>
    </div>
</template>
<script>
import Swal from 'sweetalert2';
import { products } from '@/components/get-products.vue'

export default {
    name: "Footer_page",
    methods: {
        autority() {
            let senha = window.prompt('Senha')
            if (senha == 1532) {
                window.open('http://127.0.0.1:5500/Funcion%C3%A1rio/Index.html')
            }else{
                alert('Fuckyou')
            }
        },
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
        pedido() {
            Swal.fire({
                position: 'top-end',
                title: 'PEDIDO REALIZADO!',
                type: 'success',
                text: 'enviado para o seu ZAP-ZAP (69)4002-8922, favor aguardar resposta...',
                showConfirmButton: false,
                background: '#fff',
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
li{
    text-align: left;
    font-family: cursive;
    color: brown;
}

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
    background-color: #e69e9e83;
    justify-content: space-around;
    width: 100%;
    height: 60px;
}

img {
    border-radius: 30px;
}
</style> 