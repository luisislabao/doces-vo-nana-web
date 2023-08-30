<script>



const newProducts = [{"id":1,"name":"Bolo de Chocolate","Quantitie":10,"price":120.51,"imgID":"","categories":[{"id":1,"name":"Bolos"}]},
                    {"id":2,"name":"Brownie","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bolos"}]},
                    {"id":3,"name":"Brigadeiro","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Doces"}]},
                    {"id":4,"name":"Quindim","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Doces"}]},
                    {"id":4,"name":"Coca 250ml","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bebidas"}]},
                    {"id":4,"name":"Pepsi 250ml","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bebidas"}]},
                    {"id":4,"name":"Biri 250ml","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bebidas"}]},
                    {"id":4,"name":"Fanta 250ml","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bebidas"}]},
                    {"id":4,"name":"Dolly 250ml","Quantitie":10,"price":45.5,"imgID":"","categories":[{"id":2,"name":"Bebidas"}]}]
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