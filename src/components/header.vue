<template>
    <div class="container">
        <img @click="menu()" @mouseenter="colorin('menu')" @mouseleave="colorout('menu')" id="menu"
            src="../assets/icons8-cardápio-512.png">

        <div>
            <img src="../assets/instagram.png" @click="insta('https://www.instagram.com/bolosdavonana/')"
                @mouseenter="colorin('logo')" @mouseleave="colorout('logo')" id="logo">
            <p class="instabuttom"> Bolos da Vó Nana</p>
        </div>

        <div>
            <img @click="cesta()" @mouseenter="colorin('cesta')" @mouseleave="colorout('cesta')" id="cesta"
                src="../assets/cesta-64.png">
        </div>

        <button class="shopButton" @click="pedido()" type="button">Fazer pedido!!</button>

        <!-- menu flutuante -->
        <div @mouseleave="close()" id="myDropdown" class="dropdown-content">
            <p class="funcionario" @click="autority()">Funcionário</p><br>
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
// import axios from 'axios'

export default {
    name: "HelloWorld",
    props: {
        pedidos: String
    },
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
            let contact = document.getElementById('contact').value
            let alert = ''
            let cesta = []
            let cont = ''
            if (name == '') {
                alert = '° Nome'
            } if (addres == '') {
                alert += '\n° Endereço'
            } if (contact == '') {
                alert += '\n° Contato (Whatsapp)'
            } if (name == '' || addres == '' || contact == '') {
                window.alert(`Faltam informações, tais quais:\n${alert}`)
            } else {
                let basket = JSON.parse(localStorage.getItem('cesta'))
                for (let iten in basket) {
                    if (cesta.indexOf(basket[iten][0]) == -1) {
                        cesta.push(basket[iten][0])
                    }
                } window.alert(cesta)
                console.log(basket)
                for (let tipo in cesta) {
                    for (let reg in basket) {
                        if (cesta[tipo] == basket[reg][0]) {
                            cont += (`°\n ${basket[reg][1]} - ${basket[reg][2]} x ${basket[reg][3]} =\n` + Number(basket[reg][2][0]) * basket[reg][3])
                        }
                    }
                }
                Swal.fire({
                    type: 'info',
                    title: 'CESTA ',
                    text: cont,
                    width: 250
                    
                })
            }


        },
        menu() {
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

.funcionario {
    font-size: medium;
}

.funcionario:hover {
    cursor: no-drop;
}

p {
    color: #ffe4c4;
    font-family: cursive;
    font-size: x-large;
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