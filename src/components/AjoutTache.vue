<template>
    <b-row class="ajout">
        <form @submit="ajoutTache">
            <b-col class="pl-0">
                <label class="inputText" for="texte-tache">Votre tâche: </label>
                <b-form-input id="texte-tache" class="inputText mb-2" v-model="titre" name="titre" type="text" placeholder="Ajouter une tâche" />
            </b-col>
            <b-col class="pl-0">
                <label class="inputText" for="date-de-fin">À compléter pour le: </label>
                <b-form-datepicker id="date-de-fin" v-model="date" class="mb-2"></b-form-datepicker>
            </b-col>
            <b-col class="pl-0">
                <input  class="btnSoumettre" type="submit" value="Soumettre">
                <!-- <button type="submit" value="submit" class="bouton">
                    <font-awesome-icon id="ajouter" icon="share" />
                </button> -->
            </b-col>
        </form>
    </b-row>
</template>

<script>
import  { v4 as uuidv4 } from 'uuid'; /*Ajout pour créer des ID aléatoire*/
export default {
    name:"AjoutTache",
    data () {
        return {
            titre: '',
            date: '',
        }
    },
    // Créer un nouvel objet, tâche, et le retourner dans l'App.vue
    methods: {
        ajoutTache(e) {
            e.preventDefault();
            const nouvelleTache = {
                id: uuidv4(),
                tache: this.titre,
                termine: false,
                urgent: false,
                dateFin: this.date,
            }
            this.$emit('ajout-tache', nouvelleTache);
            // Effacer l'input une fois la nouvelle tâche ajoutée.
            this.titre = '';
        }
    }    
}
</script>

<style scoped>
    .ajout {
        display: flex;
        justify-content: start;
        align-items: center;
        width: 100%;
        margin: 1% 0% 1% 0%;
    }
    .inputText {
        font-family: 'Poppins', sans-serif;
    }

    .btnSoumettre { 
        display: inline-block;
        border: none;
        border-radius: 10px;
        background-color: #d3f3cf;
        padding: 8px 20px;
        cursor: pointer;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
        font-family: 'Rancho', cursive;
        font-size: 1.7rem;
        flex: 2;
    }
    @media screen and (max-width: 768px) {
        .ajout {
        margin: 0;
    }
    }
</style>