<template>
    <div>
        <h3>Añadir un producto</h3>
        <form @submit.prevent="submitProduct">
            <div>
                <div>
                    <label for="name">Nombre</label>
                    <input id="name" type="text" v-model="name" required>            
                </div>
                <div>
                    <label for="desc">Descripcion</label>
                    <input id="desc" type="text" v-model="desc" required>           
                </div>
                <div>
                    <label for="price">Precio</label>
                    <input id="price" type="number" v-model="price" min="0" required>          
                </div>
            </div>
            <input type="submit" value="Añadir Producto">
        </form>

    </div>
</template>
<script>
export default {
    name: 'form',
    data() {
        return{
            name: '',
            desc: '',
            price: 0
        }
        
    },
    emits:[
        'submit'
    ],
    methods: {
        submitProduct(){
            this.$emit('submit', this.name, this.desc, this.price)
            this.resetForm()
        },
        resetForm(){
            this.name = ''
            this.desc = ''
            this.price = 0
        }
    },
    
}
</script>
<style>
    
</style>