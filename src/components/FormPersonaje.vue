<script>
export default {
  name: "FormPersonaje",
  data() {
    return {
      nombre: "",
      descripcion: ""
    }
  },
  methods: {
    enviarPersonaje() {
      if (this.nombre && this.descripcion) {
        this.$emit("agregar", {
          nombre: this.nombre,
          descripcion: this.descripcion
        })
        this.nombre = ""
        this.descripcion = ""
      } else {
        alert("Por favor, complete ambos campos.")
      }
    }
  }
}
</script>

<template>
  <div class="card shadow-sm mb-4">
    <div class="card-body">
      <h3 class="card-title mb-3">
        <i class="bi bi-person-plus me-2"></i>Agregar Personaje
      </h3>

      <div class="mb-3">
        <label class="form-label">Nombre</label>
        <input v-model="nombre" type="text" class="form-control" placeholder="Nombre del personaje" />
      </div>

      <div class="mb-3">
        <label class="form-label">Descripción</label>
        <textarea v-model="descripcion" class="form-control" rows="3" placeholder="Descripción"></textarea>
      </div>

      <button @click="enviarPersonaje" class="btn btn-success w-100">
        <i class="bi bi-plus-circle me-2"></i> Agregar
      </button>
    </div>
  </div>
</template>