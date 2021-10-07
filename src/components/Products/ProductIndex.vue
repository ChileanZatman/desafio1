<template >
    <div>
        Lista de Productos
        <form @submit.prevent="saveProduct">
            <table>
                <tr>
                    <th>Nombre</th>
                    <th>Descripcion</th>
                    <th>Precio</th>

                </tr>
                <tr v-for="(product,index) in productList" :key="index">
                    <td v-if="editIndex === index">
                        <input id="name" type="text" v-model="selectedProduct.name" required>
                    </td>
                    <td v-else>{{ product.name }}</td>
                    <td v-if="editIndex === index">
                        <input id="desc" type="text" v-model="selectedProduct.desc" required>
                    </td>
                    <td v-else>{{ product.desc }} </td>
                    <td v-if="editIndex === index">
                        <input id="price" type="number" v-model="selectedProduct.price" min="0" required>
                    </td>
                    <td v-else>{{ product.price }}</td>
                    <td v-if="editIndex === index">
                        <input type="submit" value="Guardar">
                    </td>
                    <td v-else><button @click="setEditValues(index)">Editar</button></td>
                    <td v-if="editIndex === index">
                        <button @click="cancelEdit">Cancelar</button>
                    </td>
                    <td v-else><button @click="deleteProduct(index)">Eliminar</button></td>
                </tr>
            </table>
        </form>
    </div>
</template>
<script>
export default {
    name: 'index',
    props: {
        productList: Array
    },
    data() {
        return {
            selectedProduct: '',
            editIndex: -1
        }
    },
    emits:[
        'delete',
        'edit'
    ],
    methods: {
        deleteProduct(index){
            this.$emit('delete',index)
        },
        saveProduct(){
            this.$emit('submit', this.editIndex, this.selectedProduct)
            this.editIndex = -1
        },
        setEditValues(index){
            this.editIndex = index;
            this.selectedProduct = this.productList[index];
        },
        cancelEdit(){
            this.editIndex = -1
        }
    }

}
</script>
<style>
    
</style>