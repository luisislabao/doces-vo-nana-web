<template>
    <div class="container">

        <div style="font-family: cursive; color: #e69e9e8a;">
            <button class="shopButton">Entrar
            </button>
            |
            <p style="color: bisque;">ou</p>
            |
            <button class="shopButton">Criar</button>
        </div>

        <div>
            <img src="../assets/instagram.png" @click="insta('https://www.instagram.com/bolosdavonana/')" id="logo">
            <p class="instabuttom"> Bolos da Vó Nana</p>
        </div>

        <div>
            <img @click="cesta()" id="menu" src="../assets/cesta-64.png">
            <div @mouseleave="close()" to id="myDropdown" class="dropdown-content">
                <ul v-for="(array) in cont" :key="array">
                    <li v-if="array[2][0] != '0'" style="color: brown;">
                        <p style="color: bisque;">{{ array[1] }} X ({{ array[2] }} Unidades) = {{ (array[2] *
                            array[3]).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }) }}
                            <button id="ex" @click="excluir(`${array[1]}`)"> X</button>
                        </p>
                    </li>
                    <li v-else>Vazio</li>
                </ul>
                <h1>Total = {{ soma.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }) }}</h1>
            </div>
        </div>

        <button class="shopButton" @click="pedido()" type="button">Fazer pedido!!</button>

        <!-- menu flutuante -->

    </div>
</template>
<script>
import Swal from 'sweetalert2';
// import axios from 'axios'

export default {
    name: "HelloWorld",
    data() {
        return {
            cont: [],
            soma: 0,
            Loggin: true
        }
    }
    ,
    methods: {
        entrar() {
            document.getElementById("myCreateAcount").classList.toggle("show");
        },
        autority() {
            let senha = window.prompt('Senha')
            if (senha == 1532) {
                window.open('http://127.0.0.1:5500/Fron-End/Funcion%C3%A1rio/Index.html')
            } else {
                alert('Fuckyou')
            }
        },
        insta(x) {
            window.open(x)
        },
        cesta() {
            let alert = ''
            this.soma = 0
            if (!this.Loggin) {
                window.alert(`Faltam informações, tais quais:\n${alert}`)
            } else {
                let basket = JSON.parse(localStorage.getItem('cesta'))
                this.cont = basket
                for (let iten in this.cont) {
                    this.soma += this.cont[iten][3] * this.cont[iten][2]
                }
            }
            console.log(this.cont)
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
        },
        excluir(nome) {
            let pkg = JSON.parse(localStorage.getItem('cesta'))
            let newpkg = []
            for (let iten in pkg) {
                if (pkg[iten][1] != nome) {
                    newpkg.push(pkg[iten])
                }
            }
            localStorage.setItem('cesta', JSON.stringify(newpkg))
            this.cesta()
            document.getElementById("myDropdown").classList.toggle("show");
        }
    }
}
</script>
<style scoped>
.instabuttom {
    color: brown;
}

li {
    color: brown;
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
    background-color: #e99f9f0c;
    border-radius: 20px;
}

img:hover {
    background-color: #ffe4c4;
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
    box-shadow: 10px 18px 16px 10px rgba(0, 0, 0, 0.363);
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

#ex {
    border-radius: 20px;
    background-color: beige;
    color: brown;
}

#ex:hover {
    background-color: brown;
    color: beige;
}

/* <!-- seetalert style --> */
</style> 