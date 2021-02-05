<template>
    <div>
        <ul class="list-group">
            <h2>Carrito</h2>
            <div class="card p-3 my-4">
                <h4>Total: ${{total}}</h4>
                <button :disabled="items.length === 0" @click="$emit('pago')" class="btn btn-info form-contol">
                    Pagar Ahora
                </button>
            </div>

            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{item.titulo}} - ${{item.precio}}
                <button  class="btn badge badge-danger float-right" @click="removerItem(item)">Eliminar</button>
            </li>
        </ul>
        </div>


</template>

<script>
export default {
    name:'Carrito',
    props:['items'],
    computed:{
        total(){
            return this.items.reduce((acumulador, item) => acumulador + Number(item.precio),0);
        }
    },
    methods: {
        removerItem(item){
            this.$emit('removerItem', item);
        }
    },
}
</script>