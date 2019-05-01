<template>
    <div class="seccion">
        <div v-if="!pago && boletos == 0" class="mensaje informacion">
            selecciona al menos un boleto.
        </div>
        <div v-else-if="!pago && boletos > 0" class="mensaje advertencia">
            Recuerda completar tu compra
        </div>    
        <div v-else class="mensaje exito">
            ¡Bienvenido!
        </div>
        <div class="atributo">
            <span class="boletos">Boletos</span>
        </div>
        <div class="atributo">
            <span class="boletos">{{boletos}}</span>
        </div>
        <div v-show="boletos > 0" class="atributo">
            <span>Total ${{total}}</span>
        </div>
        <div class="atributo">
            <!--v-on:click puede ser reemplazado por @click-->
            <button v-on:click="actualizarCantidad(1)">+</button>
            <button @click="actualizarCantidad(-1)">-</button>
        </div>
        <div v-if="!pago && boletos" class="atributo">
            <button v-on:click="pago=true">Pagar</button>
        </div>
        <div v-if="pago" class="atributo">
            <button v-on:click="reiniciar">Reiniciar</button>
        </div>
        <div class="atributo">
            <span class="comision" :class="clase_comision">${{comision}}</span>
        </div>
    </div>
</template>

<script>
export default {
    
    data(){
        return{
            boletos:0,
            comision: 0,
            clase_comision:"neutro",
            pago:false
        }
    },
    computed:{
        total(){
            return this.boletos * 100;
        }
    },
    methods: {
        actualizarCantidad(cantidad){
            this.boletos += cantidad;

            if(this.boletos>10){
                this.boletos = 10;
            }else if(this.boletos<0){
                this.boletos=0;
            }
        },
        reiniciar(){
            this.pago=false;
            this.boletos=0;
            this.comision=0;
            
        }
    },
    watch: {
        boletos(newValue, oldValue){
            if(newValue>oldValue){
                this.comision +=10;
                this.clase_comision="incremento";
            }else{
                this.comision-=15;
                this.clase_comision="decremento";
            }

            if(this.comision<0){
                this.comision = 0;
                this.clase_comision="neutro";
            }
        }
    },
}
</script>
<style>
.boletos{
    font-size: 4rem;
    font-weight: bold;
}
.comision{
    font-size: 2.2rem;
}
.neutro{
    color:#2a2a2a;
}
.incremento{
    color: green;
}
.decremento{
    color:red;
}

.mensaje{
    border-radius: 5px;
    border-width: 4px;
    border-style: dashed;
    padding: 10px;
    font-size: 2.1rem;
    font-weight: bold;
}
.informacion{
    border-color: blue;
}
.advertencia{
    border-color: orange;
}
.exito{
    border-color: green;
}
</style>
