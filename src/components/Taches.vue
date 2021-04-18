<template>
  <div>
      <div v-for="tache in taches" v-bind:key="tache.id">
          <Tache v-bind:tache="tache" v-on:sup-tache="$emit('sup-tache', tache.id)"/> <!--v-bind passe en props mes taches vers le component Tache.vue *** v-on accepte l'ID de ma suppresion -->
      </div>
  </div>
</template>

<script>
import Tache from "./Tache"
export default {
    name:"Taches",
    components: {
        Tache,
    },
    props:["taches"]/*je viens chercher mes props de mon component App.vue */
}
</script>

<style scoped>

</style>