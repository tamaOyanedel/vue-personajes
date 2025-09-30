<script setup>
import { ref, computed, onMounted } from "vue";
import FormPersonaje from "./components/FormPersonaje.vue"
import ListaPersonajes from "./components/ListaPersonajes.vue"

// Carga data desde el Json
onMounted(async () => {
  try {
    const response = await fetch("/pokemones.json");
    const data = await response.json();
    personajes.value = data[0].pokemones;
  } catch (error) {
    console.error("Error cargando los pokemones:", error);
  }
});

// Lista de personajes
const personajes = ref([]);

// Búsqueda
const search = ref("");

// Computed para filtrar
const personajesFiltrados = computed(() => {
  if (!search.value) return personajes.value;
  return personajes.value.filter((p) =>
    p.nombre.toLowerCase().includes(search.value.toLowerCase())
  );
});

// Mensaje de error si no existe
const noExiste = computed(() => personajesFiltrados.value.length === 0);

// Método para agregar nuevo personaje
const agregarPersonaje = (personaje) => {
  personajes.value.push({
    id: Date.now().toString(),
    ...personaje
  });
};
</script>

<template>
  <div class="container py-4">
    <h1 class="text-center">Lista de Pokemones</h1>

    <!-- Formulario -->
    <FormPersonaje @agregar="agregarPersonaje" />

    <!-- Buscador -->
    <div class="mb-4">
      <label class="form-label">Buscar Pokémon</label>
      <input v-model="search" type="text" class="form-control" placeholder="Ej: Pikachu" />
    </div>

    <!-- Mensaje si no existe -->
    <p v-if="noExiste" class="text-danger fw-bold">
      El pokemon que desea buscar no existe.
    </p>

    <!-- Componente Lista -->
    <ListaPersonajes :personajes="personajesFiltrados" />
  </div>
</template>