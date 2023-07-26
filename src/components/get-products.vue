<script>
// const products = {
//     "Doces": 
//     [
//         {'Id': 0, "nome": 'Quindim', "tipo": "Doces", "price": 0, "quantidade": 10 },
//         {'Id': 0, "nome": 'Brigad.', "tipo": "Doces", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'P.coco', "tipo": "Doces", "price": 0, "quantidade": 0 }
//     ],
//     "Bolos":
//     [
//         {'Id': 0, "nome": 'Bolo P', "tipo": "Bolos", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'Bolo M', "tipo": "Bolos", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'Bolo G', "tipo": "Bolos", "price": 0, "quantidade": 0 }
        
//     ],
//     "Salgados":
//     [
//         {'Id': 0, "nome": 'Empada de F', "tipo": "Salgados", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'Hamburger', "tipo": "Salgados", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'HotDog', "tipo": "Salgados", "price": 0, "quantidade": 0 }
//     ],
//     "Bebidas":
//     [
//         {'Id': 0, "nome": 'Coca250ml', "tipo": "Bebidas", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'Pepsi250ml', "tipo": "Bebidas", "price": 0, "quantidade": 0 },
//         {'Id': 0, "nome": 'Fanta250ml', "tipo": "Bebidas", "price": 0, "quantidade": 0 },
        
//     ]
// }



const newProducts = [{"id":1,"name":"Bolo de Chocolate","description":"Lorem impsum Lorem impsum Lorem impsum","price":120.5,"imgID":"","categories":[{"id":1,"name":"Cakes"}]},
                    {"id":2,"name":"Brownie","description":"Lorem impsum Lorem impsum Lorem impsum","price":45.5,"imgID":"","categories":[{"id":2,"name":"Candys"}]},
                    {"id":3,"name":"Browni","description":"Lorem impsum Lorem impsum Lorem impsum","price":45.5,"imgID":"","categories":[{"id":2,"name":"Candys"}]},
                    {"id":4,"name":"Quindim","description":"Lorem impsum Lorem impsum Lorem impsum","price":45.5,"imgID":"","categories":[{"id":2,"name":"Candys"}]},]
export {newProducts}
export default{
    name: "GetProducts",
    data (){
        return{
            newProducts
        }
    }
}
</script>