<template>
  <div class="container">
    <form class="cajaFormulario">
      <div class="row d-flex align-items-center">
        <div class="col-2">
          <label :class="{ 'color-cambiado': pacienteColor }">Paciente</label>
        </div>
        <div class="col-2">
          <label :class="{ 'color-cambiado': fechaColor }">Fecha</label>
        </div>
        <div class="col-2">
          <label :class="{ 'color-cambiado': horaColor }">Hora</label>
        </div>
        <div class="col-2">
          <label :class="{ 'color-cambiado': gravedadColor }">Gravedad</label>
        </div>
        <div class="col-2">
          <label :class="{ 'color-cambiado': motivoColor }">Motivo</label>
        </div>
      </div>

      <div class="row d-flex align-items-center">
        <div class="col-2">
          <input v-model="formData.paciente" @change="cambioColorLabel('pacienteColor')" type="text" class="me-2" />
        </div>
        <div class="col-2">
          <input v-model="formData.fecha" @change="cambioColorLabel('fechaColor')" type="date" />
        </div>
        <div class="col-2">
          <input v-model="formData.hora" @change="cambioColorLabel('horaColor')" type="time" class="me-2" />
        </div>
        <div class="col-2">
          <select v-model="formData.gravedad" @change="cambioColorLabel('gravedadColor')">
            <option>Baja</option>
            <option>Media</option>
            <option>Alta</option>
          </select>
        </div>
        <div class="col-2">
          <input v-model="formData.motivo" @change="cambioColorLabel('motivoColor')" type="text" class="me-2" />
        </div>
      </div>

      <div class="mt-3">
        <button id="botoncin" type="button" @click="agregarTarjeta">Agregar</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'CheckForm',
  data() {
    return {
      pacienteColor: false,
      fechaColor: false,
      horaColor: false,
      gravedadColor: false,
      motivoColor: false,
      formData: {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: 'Baja',
        motivo: ''
      }
    };
  },
  methods: {
    cambioColorLabel(label) {
      this[label] = !this[label];
    },
    agregarTarjeta() {
      this.$emit('agregar-tarjeta', { ...this.formData });
      this.resetForm();
    },
    resetForm() {
      this.formData = { paciente: '', fecha: '', hora: '', gravedad: 'Baja', motivo: '' };
    }
  }
};
</script>

<style scoped>
.cajaFormulario {
  border: solid black 3px;
  border-radius: 20px;
  margin: 0 auto;
}

.color-cambiado {
  color: red; 
}

#botoncin {
  width: 100px;
}
</style>
