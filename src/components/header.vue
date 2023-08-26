<template>
    <div class="container">
        <div>
            <img @click="cesta()"  @mouseenter="colorin('menu')" @mouseleave="colorout('menu')" id="menu"
            src="../assets/cesta-64.png">
            <div @mouseleave="close()" id="myDropdown" class="dropdown-content">
                    <ul v-for="(array) in cont" :key="array">
                        <li v-if="array[2][0] != '0'"><p>{{ array[1]}} (X{{ array[2][0]}}) - {{ array[3]}}</p></li> 
                    </ul>
            </div>
        </div>

        <div>
            <img src="../assets/instagram.png" @click="insta('https://www.instagram.com/bolosdavonana/')"
                @mouseenter="colorin('logo')" @mouseleave="colorout('logo')" id="logo">
            <p class="instabuttom"> Bolos da Vó Nana</p>
        </div>

        <!-- <div class="cesta">
            <img @click="cesta()" @mouseenter="colorin('cesta')" @mouseleave="colorout('cesta')" id="cesta" src="../assets/cesta-64.png"
                >
        </div> -->

        <button class="shopButton" @click="pedido()" type="button">Fazer pedido!!</button>

        <!-- menu flutuante -->

    </div>
</template>
<script>
import Swal from 'sweetalert2';
// import axios from 'axios'

export default {
    name: "HelloWorld",
    props: {
        pedidos: String
    },
    data() {
        return {
            cont: []
        }
    }
    ,
    methods: {
        autority() {
            let senha = window.prompt('Senha')
            if (senha == 1532) {
                window.open('http://127.0.0.1:5500/Fron-End/Funcion%C3%A1rio/Index.html')
            } else {
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
            let name = document.getElementById('name').value
            let addres = document.getElementById('addres').value
            let alert = ''
            // let cesta = []
            if (name == '') {
                alert = '° Nome/Id'
            } if (addres == '') {
                alert += '\n° Senha'
            } if (name == '' || addres == '') {
                window.alert(`Faltam informações, tais quais:\n${alert}`)
            } else {
                let basket = JSON.parse(localStorage.getItem('cesta'))
                this.cont = basket
            }
            document.getElementById("myDropdown").classList.toggle("show");


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
.instabuttom {
    color: brown;
}

li {
    color:brown;
    font-family: cursive;
    /* font-size: x-large; */
    text-align: left;
}

div {
    display: flex;
    border-radius: 20px;
}

.container {
    display: flex;
    background-color: #e69e9e8a;
    justify-content: space-around;
    width: 100%;
    height: 60px;
}

img {
    max-width: 400px;
    max-height: 60px;
    background-color: #e99f9fe0;
    border-radius: 20px;

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
/* <!-- seetalert style --> */
</style> 