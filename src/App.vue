<script>
import FormPersonaje from "./components/FormPersonaje.vue"
import ListaPersonajes from "./components/ListaPersonajes.vue"

export default {
  name: "App",
  components: {
    FormPersonaje,
    ListaPersonajes,
  },
  data() {
    return {
      personajes: [
        { id: "1", nombre: "Pikachu", descripcion: "Un ratón eléctrico muy amigable ⚡" },
        { id: "2", nombre: "Kakuna", descripcion: "Un Pokémon capullo que evoluciona en Beedrill 🐝" },
        { id: "3", nombre: "Beedrill", descripcion: "Un Pokémon abeja con aguijones peligrosos 🐝⚔️" },
        { id: "4", nombre: "Metapod", descripcion: "Un capullo verde que solo conoce 'Endurecer' 🟢" },
        { id: "5", nombre: "Rattata", descripcion: "Una pequeña rata muy rápida 🐭" }
      ]
    }
  },
  methods: {
    agregarPersonaje(personaje) {
      this.personajes.push({
        id: Date.now().toString(),
        ...personaje
      })
    }
  }
}
</script>

<template>
  <div class="container py-4">
    <h1 class="text-center">Lista de Personajes</h1>

    <!-- Formulario -->
    <FormPersonaje @agregar="agregarPersonaje" />

    <!-- Componente Lista -->
    <ListaPersonajes :personajes="personajes" />
  </div>
</template>