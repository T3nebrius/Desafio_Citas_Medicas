<template>
  <div>
    <CheckForm @agregar-tarjeta="agregarTarjeta" />
    <div v-for="(tarjeta, index) in tarjetas" :key="index">
      <CardInfo
        :paciente="tarjeta.paciente"
        :fecha="tarjeta.fecha"
        :hora="tarjeta.hora"
        :gravedad="tarjeta.gravedad"
        :motivo="tarjeta.motivo"
        @eliminar="eliminarTarjeta(index)"
      />
    </div>
  </div>
</template>

<script>
import CheckForm from './components/CheckForm.vue';
import CardInfo from './components/CardInfo.vue';

export default {
  name: 'App',
  components: {
    CheckForm,
    CardInfo
  },
  data() {
    return {
      tarjetas: []
    };
  },
  methods: {
    agregarTarjeta(datos) {
      console.log(datos);
      this.tarjetas.push(datos);
    },
    eliminarTarjeta(index) {
      this.tarjetas.splice(index, 1);
    }
  }
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
