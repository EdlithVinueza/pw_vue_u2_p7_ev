<template>
     <img :src="imagen" alt="No se puede ver">
    <div class="seccion-pregunta">
        <input v-model="pregunta" type="text" placeholder="Hazme una Pregunta">
        <p>Recuerda que cuando finalices tu pregunta dar un ?</p>
        <h1>{{ pregunta }}</h1>
        <h2>{{ respuesta }}</h2>
    </div>

</template>

<script>
export default {
    data() {
        return { //Declaramos las propiedades reactivas
            pregunta: 'Hola Mundo',
            respuesta: null,
            imagen: 'https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif'
        }
    },
    watch: { //observadores de propiedades reactivas 
        pregunta(value, oldValue) { //debe tener el mismo nombre de la propiedad reactiva a observar
            console.log(value);
            console.log(oldValue);
            if (value.includes('?')) {
                //llamar a ala API para obtener el si y el no
                this.fachada();
            }
        }
    },
    methods: {
        async llamarAPI() { //metodo asincrono porel await
            console.log('AQUI LLAMO AL API');
            const data = await fetch('https://yesno.wtf/api').then(respuesta => respuesta.json());
            this.respuesta = data.answer;
            this.imagen = data.image;
            console.log(data);
        },
        async fachada() {  //metodo asincrono por el await
            await this.llamarAPI();
        }
    }
}
</script>

<style>
img {
    max-height: 100%;
    height: 100vh;
    max-width: 100%;
    width: 100vw;
    position: fixed;
    top: 0px;
    left: 0px;
}
.seccion-pregunta{
    position:relative; 
    text-align: center;
}
h1,p,h2{
    color: white ;   
}
p{
    font-size: 30px;
}

input {
margin-top: 35%;
width: 260px;
padding: 15px 30px;
border: none;
border-radius: 7px;
font-size: 18px;
}
</style>