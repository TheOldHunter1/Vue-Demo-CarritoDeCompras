<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-tittle">{{producto.titulo}}</h5>
            <img :src="producto.imagen" width="150" height="200">
            <p class="text-center text-muted card-text display-4">${{Number(producto.precio).toFixed()}}</p>
            <button @click="agregarCarro(producto)" class="btn btn-primary form-control" :class="{'btn-warning':estaEnCarrito}" :disabled="estaEnCarrito">
                {{ estaEnCarrito ? 'Agregado' :'Agregar al carrito'}}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name:'Producto',
    props: ['producto', 'estaEnCarrito'],
    methods: {
        agregarCarro(producto){
            this.$emit('agregar-carro', producto);
        }
    },
}
</script>

<style>
    
</style>