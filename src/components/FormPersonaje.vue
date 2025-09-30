<script setup>
import { ref } from "vue";

const emit = defineEmits(["agregar"]);

const nombre = ref("");
const descripcion = ref("");

// Validación y envío
const enviarPersonaje = () => {
  if (!nombre.value.trim() || !descripcion.value.trim()) {
    alert("⚠️ Por favor, complete ambos campos.");
    return;
  }

  emit("agregar", {
    nombre: nombre.value,
    descripcion: descripcion.value
  });

  // Reset
  nombre.value = "";
  descripcion.value = "";
};
</script>

<template>
  <div class="card shadow-sm mb-4">
    <div class="card-body">
      <h3 class="card-title mb-3">
        <i class="bi bi-person-plus me-2"></i>Agregar Pokemón
      </h3>

      <div class="mb-3">
        <label class="form-label">Nombre</label>
        <input v-model="nombre" type="text" class="form-control" placeholder="Nombre del pokemón" />
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