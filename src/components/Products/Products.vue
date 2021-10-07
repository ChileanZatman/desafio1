<template>
    <div>
        <ProductForm @submit="addProduct"/>
        <ProductIndex :productList="productList" @delete="removeProduct" @edit="editProduct"/>
    </div>
</template>
<script>
import ProductForm from './ProductForm.vue'
import ProductIndex from './ProductIndex.vue'
export default {
    components: {
        ProductForm,
        ProductIndex
    },
    name: 'Products',
    data() {
        return {
            productList: []
        }
    },
    methods: {
        addProduct(name, desc, price){
            const product = {
                name: name,
                desc: desc,
                price: price
            }
            this.productList.push(product)
        },
        removeProduct(index){
            const confirm = window.confirm('¿Estás seguro de eliminar la tarea?');
            if (confirm) this.productList.splice(index, 1);
        },
        editProduct(index, product){
            this.productList[index] = product
        }
    },
    
}
</script>
<style>
    
</style>