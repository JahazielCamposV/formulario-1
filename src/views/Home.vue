<template>
  <form @submit.prevent="procesarForm">
    <input 
      type="text"
      class="form-control my-2"
      placeholder="Ingrese nombre"
      v-model.trim="objForm.nombre"
    >
    <input 
      type="text"
      class="form-control my-2"
      placeholder="Ingrese descripcion"
      v-model.trim="objForm.descripcion"
    >
    <div class="form-check form-check-inline">
      <input 
        id="check1"
        type="checkbox"
        class="form-check-input"
        v-model="objForm.categorias"
        value="java"
      >
      <label for="check1" class="form-check-label">NodeJS</label>
    </div>
    <div class="form-check form-check-inline">
      <input 
        id="check2"
        type="checkbox"
        class="form-check-input"
        v-model="objForm.categorias"
        value="nodejs"
      >
      <label for="check2" class="form-check-label">Java</label>
    </div>
    <div class="mt-2">
      <div class="form-check form-check-inline">
        <input 
          id="radio1"
          type="radio"
          class="form-check-input"
          v-model="objForm.estado"
          value="urgente"
        >
        <label for="radio1" class="form-check-label">Urgente</label>
      </div>
      <div class="form-check form-check-inline">
        <input 
          id="radio2"
          type="radio"
          class="form-check-input"
          v-model="objForm.estado"
          value="relax"
        >
        <label for="radio2" class="form-check-label">Relax</label>
      </div>
    </div>
    <div class="mt-2">
      <input 
        type="number"
        class="form-control my-2"
        v-model.number="objForm.numero"
      >
    </div>
    <button 
      class="btn btn-dark mt-2 btn-block" 
      type="submit"
      :disabled="bloquear"
    >
    Procesar
    </button>
  </form>
  <!-- <p>
    {{ objString }}
  </p> -->
  <hr>
  <p>
    {{ objForm }}
  </p>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      objForm: {
        nombre: '',
        descripcion: '',
        categorias:[],
        estado: '',
        numero: 0
      }
    }
  },
  computed: {
    objString(){
      return JSON.stringify(this.objForm)
    },
    bloquear(){
      return (this.objForm.nombre.trim() && this.objForm.descripcion.trim()) === "" ? true : false
    }

  },
  methods: {
    procesarForm(){
      if (this.objForm.nombre.trim() === "") {
        console.log('Campo vacio')  
        return
      }
      console.log(this.objForm)

      this.objForm = {
        nombre: '',
        descripcion: '',
        categorias:[],
        estado: '',
        numero: 0
      }
    }
  }
}
</script>
