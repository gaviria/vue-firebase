<template>
    <div class="seccion">
        <div class="atributo">
            <input v-model="email" @keyup.enter = "actualizarEmail" type="text" name="email" id="email">
        </div>
    </div>
</template>

<script>
export default {
    props:['emailRecibido'],
    data(){
        return{
            email:''
        }
    },
    methods: {
        actualizarEmail(event){
            
        }
    },
    created() {
        this.email = this.emailRecibido
    },
}
</script>
<style>
.email{
    text-align: left;
}
</style>
