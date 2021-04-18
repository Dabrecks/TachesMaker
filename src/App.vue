<template>
    <div id="app">
        <Header />
        <AjoutTache v-on:ajout-tache="ajouterTache" />    <!--v-on pour aller chercher notre nouvelle tâche et déclencher la fonction ajouterTache-->
        <Taches v-bind:taches="taches" v-on:sup-tache="suprimerTache" />     <!--v-bind pour envoyer ma liste vers le component Taches.vue en props **** v-on pour aller chercher mon ID de supression et déclencher la fonction suprimerTache-->
    </div>
</template>

<script>

import Taches from "./components/Taches"
import Header from "./components/layout/Header"
import AjoutTache from "./components/AjoutTache"
export default {
  name: 'App',
  components: {
    Taches,
    Header,
    AjoutTache

  },
  data () {
    return {
      taches: [
        {
          id: 1,
          tache: "Aspirateur",
          termine: false,
          urgent: false,
          dateFin: "21-04-2021",
        },
        {
          id: 2,
          tache: "Dentiste",
          termine: false,
          urgent: false,
          dateFin: "18-04-2021",
        },
        {
          id: 3,
          tache: "Pratique baseball",
          termine: false,
          urgent: false,
          dateFin: "21-04-2021",
        },
        {
          id: 4,
          tache: "Payer factures cell",
          termine: false,
          urgent: false,
          dateFin: "21-04-2021",
        }
      ]
    }
  },
  methods: {
    // Supression de la tâche
    suprimerTache (id) {
      this.taches = this.taches.filter(tache => tache.id !== id);
    },
    //Ajouter une tâche passée par le component ajoutTache.vue avec le spread operator
    ajouterTache (nouvelleTache) {
      this.taches = [...this.taches, nouvelleTache];
    }
  }
}
</script>

<style>
/* Rancho */
/* font-family: 'Rancho', cursive; */
@import url('https://fonts.googleapis.com/css2?family=Rancho&display=swap');
/* Poppins */
/* font-family: 'Poppins', sans-serif; */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');


  * {
      margin: 0;
      padding: 0;
  }
  body {
    background-image: linear-gradient(to bottom right, #4CA9DF, #A1FFB3);
    font-family: sans-serif;
    line-height: 1.4;
    padding: 3% 5% 3% 5%;
  }
</style>
