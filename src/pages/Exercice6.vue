<template>
  <v-container max-width="700">
    <!-- Données de l'exercice -->
    <exercice-objectifs number="6"/>
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <v-card
        class="mx-auto my-6 pa-2"
        max-width="500"
      >
        <v-text-field
          label="Nouvelle tâche"
          clearable
        >
          <template v-slot:append-inner>
            <v-btn>Ajouter</v-btn>
          </template>
        </v-text-field>

        <v-card-title>Liste des tâches</v-card-title>

        <v-card-subtitle>
          Il n'y a pas de tâches... chanceux ! 😄
        </v-card-subtitle>

        <v-list>
          <v-list-item>
            <template v-slot:prepend>
              <v-list-item-action start>
                <v-checkbox-btn />
              </v-list-item-action>
            </template>

            <v-list-item-title>
              *** Titre de la tâche ***
            </v-list-item-title>

            <v-list-item-subtitle>
              Créé le *** Date ***
              à *** Heure ***
            </v-list-item-subtitle>
          </v-list-item>
        </v-list>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
// Importation du composant ExerciceObjectifs
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";
// Importation de la fonction réactive ref
import {ref} from 'vue';

// Tableau réactif de tâches
const tasks = ref([
  {
    "title": "Acheter du Lait",
    "completed": false,
    "date": 1738162351961
  },
  {
    "title": "Nettoyer le four",
    "completed": false,
    "date": 1737978751912
  },
  {
    "title": "Acheter de l'aspirine",
    "completed": true,
    "date": 1737856351933
  }
]);
// Nouvelle tâche à ajouter
const newTask = ref("*** Nouvelle tâche ***");

/**
 * Fonction qui ajoute une nouvelle tâche à la liste.
 */
function addTask () {
  // Ajout de la nouvelle tâche
  tasks.value.push({
    "title": newTask.value,
    "completed": false,
    "date": Date.now() // Date actuelle au format timestamp
  });
  // Réinitialisation de la saisie
  newTask.value = "";
}
</script>

<style scoped lang="sass">

</style>
