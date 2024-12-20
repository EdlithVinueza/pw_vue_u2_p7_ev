<template>
    <h2>{{ encabezado }} : {{ valor2 }}</h2>
    <p>{{ numero }} <sup>2</sup> = {{ calcularCuadradoComputada }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calcularCuadradoComputada }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calcularCuadradoComputada }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calcularCuadradoComputada }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calcularCuadradoComputada }}</p>
    
    <div>
        <button @click="incrementar">+1</button>
        <button v-on:click="decrementar">-1</button>
    </div>
    <div v-if="esVerdad">
        <h1>FELIZ Navidad</h1>
    </div>
</template>

<script>
export default {
   
    data() {
        return {
            numero: this.valor,
            titulo: 'Contador'
        };
    },
    methods: {
        incrementar() {
            this.numero++;
        },
        decrementar() {
            this.numero--;
        },
    },
    computed: {
        calcularCuadradoComputada() {
            console.log('Entro a calcular computada');
            return this.numero * this.numero;
        }
    },
    props: {
        encabezado: {
            type: String,
            //contega una j la palabra
            validator(value){
                return value.includes('j');
            }
        },
        valor: Number,
        valor2: {
            type: Number,
            Required:false,
            default:77,
            validator(value){
                //programo mi validacion bajo mi criterio y retorno ture cuando es valido para mi
                //retorno false cuando no es valido para mi
                return value <= 77;
            },
        },
        esVerdad: {
            type:Boolean, 
            Required:true,
        },
        arreglo:Array,
        fecha: Date,
        objetoPersona:Object,
    },
}
</script>

<style>
button {
    background: #64B687;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0px 5px; 
    padding: 5px 10px;
}

button:hover {
    background: #5aa67b;
}
</style>