<script>
export default {
  name: "ListaPersonajes",
  props: {
    personajes: {
      type: Array,
      required: true
    }
  },
  methods: {
    iconoPara(nombre) {
      const nombreLower = nombre.toLowerCase()
      if (nombreLower.includes("pikachu")) return "bi bi-lightning-charge-fill"
      if (nombreLower.includes("kakuna")) return "bi bi-bug-fill"
      if (nombreLower.includes("beedrill")) return "bi bi-bezier"
      if (nombreLower.includes("metapod")) return "bi bi-shield-fill-check"
      if (nombreLower.includes("rattata")) return "bi bi-mouse"
      return "bi bi-star-fill"
    }
  }
}
</script>

<template>
  <div class="row">
    <div v-for="personaje in personajes" :key="personaje.id" class="col-md-6 col-lg-4 mb-3">
      <div class="card h-100 shadow-sm">
        <div class="card-body">
          <h5 class="card-title d-flex align-items-center">
            <i :class="iconoPara(personaje.nombre)" class="me-2 text-primary"></i>
            {{ personaje.nombre }}
          </h5>
          <p class="card-text">{{ personaje.descripcion }}</p>
        </div>
      </div>
    </div>
  </div>
</template>