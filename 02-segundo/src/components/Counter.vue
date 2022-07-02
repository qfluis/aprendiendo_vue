<template>
    <div> <!-- Eliminar -->
        
        <h2>{{ tituloCustom }}</h2>
        <p>{{cuenta}}<sup>2</sup> = {{ cuadradoComputado }}</p>
        <p>{{cuenta}}<sup>2</sup> = {{ cuadradoComputado }}</p>
        <p>{{cuenta}}<sup>2</sup> = {{ cuadradoComputado }}</p>
        <p>{{cuenta}}<sup>2</sup> = {{ cuadrado() }}</p>
        <p>{{cuenta}}<sup>2</sup> = {{ cuadrado() }}</p>
        <button v-on:click="incrementar(-1)">-1</button>
        <button @click="incrementar(1)">+1</button>
    </div>
</template>

<script>
export default {
    props:{   //['nombre','start'],
        nombre: String,
        start: {
            type: Number,
            default: 1
            //required: true
        }
    },
    name: 'Counter',
    data()  {
        return {
            cuenta: this.start //Number(this.start) || 1
        }
    },
    computed: {  // Se guardan en caché
        cuadradoComputado(){
            console.log("cuadradoComputado")
            return this.cuenta * this.cuenta
        },
        tituloCustom(){
            return this.nombre || 'Contador genérico'
        }

    },
    methods: {  // Se ejecuta cada vez que se llama
        cuadrado(){
            console.log("cuadrado")
            return this.cuenta * this.cuenta
        },
        incrementar(paso){
            this.cuenta+=paso
        }
    },  
}
</script>

<style>

</style>
