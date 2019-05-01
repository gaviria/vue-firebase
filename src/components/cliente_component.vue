<template>
    <div class="seccion">
        <div class="atributo">
            <span>{{nombreCompleto}}</span>
        </div>
        <div class="atributo">
            <!--v-bind:src es lo mismo que :src -->
            <img v-bind:src="foto_perfil" alt="">
        </div>
        <div class="atributo">
            <a :href="biografia" target="_blank">Biografía</a>
        </div>
        <div class="atributo">
            <span>Edad: {{edad}}</span>
        </div>
        <div class="atributo">
            <span>
                {{email}}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    props:['email'],
    data(){
        return{
            nombres: 'Isaac',
            apellidos: 'Newton',
            fecha_nacimiento: new Date(1994,9,27),
            foto_perfil:'data:image/jpeg;base64,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',
            biografia:'https://es.wikipedia.org/wiki/Isaac_Newton'
        }
    },
    computed: {
        nombreCompleto(){
            return this.nombres + ' ' + this.apellidos;
        },
        edad(){
            return this.calcularEdad(this.fecha_nacimiento);
        }
    },
    methods: {
        calcularEdad(fecha){
            let fecha_actual = new Date();
            let diferencia = fecha_actual - this.fecha_nacimiento;
            return Math.floor(diferencia / (1000*60*60*24*365 ));
        }
    },
    created() {
        this.$emit('onCambioEmail','newton@email.com')
    },
}
</script>

<style scope>

</style>
