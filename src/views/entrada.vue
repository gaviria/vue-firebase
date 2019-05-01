<template>
  <div>
    <anuncio_component></anuncio_component>
    <cliente_component :email="email" @onCambioEmail="actualizarEmail"></cliente_component>
    <boletos_component></boletos_component>
    <email_component :emailRecibido="email" @onCambioEmail="actualizarEmail"></email_component>
    <firma_component></firma_component>
    
  </div>
</template>

<script>
import cliente_component from "@/components/cliente_component.vue";
import anuncio_component from "@/components/anuncio_component.vue";
import boletos_component from "@/components/boletos_component.vue";
import firma_component from "@/components/firma_component.vue";
import email_component from "@/components/email_component.vue";

export default {
  components: {
    cliente_component,
    anuncio_component,
    boletos_component,
    firma_component,
    email_component
  },
  data() {
    return {
      email: ""
    };
  },
  methods: {
    actualizarEmail(email) {
      this.email = email;
    }
  }
};
</script>

<style>
.seccion {
  font-size: 2.4rem;
  color: #202020;
  background-color: #e9e9e9;
  border-radius: 5px;
  margin: 10px;
  padding: 10px;
}
.atributo {
  margin: 10px;
}
</style>
