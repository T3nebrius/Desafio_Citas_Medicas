<template>
    <div :class="['card-container', colorClase]">
      <p><strong>Paciente:</strong> {{ paciente }}</p>
      <p><strong>Fecha:</strong> {{ fecha }}</p>
      <p><strong>Hora:</strong> {{ hora }}</p>
      <p><strong>Gravedad:</strong> {{ gravedad }}</p>
      <p><strong>Motivo:</strong> {{ motivo }}</p>
      <button @click="$emit('eliminar')">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CardInfo',
    props: {
      paciente: String,
      fecha: String,
      hora: String,
      gravedad: String,
      motivo: String
    },
    computed: {
      colorClase() {
        switch (this.gravedad) {
          case 'Baja':
            return 'baja';
          case 'Media':
            return 'media';
          case 'Alta':
            return 'alta';
          default:
            return '';
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .card-container {
    border: 1px solid #ccc;
    padding: 16px;
    margin: 10px 0;
    border-radius: 8px;
  }
  
  .baja {
    background-color: green;
    color: white;
  }
  
  .media {
    background-color: yellow;
    color: black;
  }
  
  .alta {
    background-color: red;
    color: white;
  }
  </style>
  