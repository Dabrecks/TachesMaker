<template>
    <b-row class="tacheLigne">
        <!-- Mes infos -->
        <b-col cols="10" lg="8" order-lg="3" class="sectionCentre">
                <div class="infoTache">
                    <div class="tache">
                        <p class="pTache m-0 pr-4">       
                            <span v-bind:class="{'complete':tache.termine}">{{tache.tache}}</span>    <!--on bind les class complete et urgent selon la tâche est terminée ou urgente-->
                        </p>
                    </div>
                </div>
                <div class="date">
                    <p class="pDate">
                       <span>{{tache.dateFin}}</span>
                     </p>
                </div>
        </b-col>
        <!-- Urgent -->
        <b-col cols="2" lg="1" order-lg="2" class="btnUrgent p-0">
             <font-awesome-icon id="urgent" class="fa-2x" v-if="tache.urgent" icon="fire" />    <!--Conditional rendering si la tâche est urgente -->
        </b-col>
        <!-- Mes checkBoxs -->
        <b-col cols="10" lg="2" order-lg="1" class="checkbox">
            <div class="checkboxTermine m-1">     <!--V-ON pour rendre les tâches terminées ou urgentes -->
                <b-form-checkbox 
                    type="checkbox"    
                    v-on:change="marqueTermine"
                    name="termine"
                >
                <label for="termine">
                   <p class="mb-0">Terminé</p> 
                </label>
                </b-form-checkbox>
            </div>
            <div class="checkboxUrgent m-1">
                <b-form-checkbox  
                    type="checkbox"    
                    v-on:change="marqueUrgent"
                    name="urgent"
                >
                <label for="urgent">
                    <p class="mb-0">Urgent</p> 
                </label>
                </b-form-checkbox>
            </div>
        </b-col>
        <!-- Suprimer -->
        <b-col cols="2" lg="1" order-lg="4" class="btnSuprimer">
            <font-awesome-icon id="suprimer" class="fa-2x" v-on:click="$emit('sup-tache', tache.id)"  icon="trash" /> <!--Envoyer l'ID à supprimer à mon component Taches.vue puis App.vue-->
        </b-col>


    </b-row>
</template>

<script>
export default {
    name:"Tache",
    props: ["tache"],
    methods: {
        // Method pour rendre terminé
        marqueTermine () {
            this.tache.termine = !this.tache.termine
        },
        // Method pour rendre urgent
        marqueUrgent () {
            this.tache.urgent = !this.tache.urgent
        }
    }
}
</script>

<style scoped>
    .tacheLigne {
        background-color: #f4f4f4;
        margin: 10px 0;
        border-bottom: 1px #ccc dotted;
        border-radius: 10px;
    }
    .sectionCentre {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: start;
    }
    .checkbox {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: start;
    }
    #urgent {
        color: #fb7878;
    }
    .pTache {
        font-size: 2rem;
        font-weight: bold;
        font-family: 'Rancho', cursive;
    }
    .pDate{
        color: grey;
        font-family: 'Rancho', cursive;
    }
    .btnSuprimer, .btnUrgent {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    #suprimer {
        color:  #4CA9DF;
    }

    /*CSS pour quand la tâche est complétée*/
    .complete {
        text-decoration: line-through solid 2px rgb(224, 63, 63);
    }

    /* MEDIA QUERY */
    @media screen and (max-width: 992px) {
        .checkbox {
            flex-direction: row;
            justify-content: start;
        }   
        #suprimer {
            margin-bottom: 10px;
        }    
    }
    @media screen and (max-width: 540px) {
        .pTache {
            font-size: 1.2rem;
            font-weight: bold;
        }
    }
</style>