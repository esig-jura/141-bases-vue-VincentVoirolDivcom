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
          v-model="newTask"
          @keyup.enter="addTask"
        >
          <template v-slot:append-inner>
            <v-btn @click="addTask">Ajouter</v-btn>
          </template>
        </v-text-field>

        <v-card-title>Liste des tâches</v-card-title>

        <v-card-subtitle v-if="tasks.length === 0">
          Il n'y a pas de tâches... chanceux ! 😄
        </v-card-subtitle>

        <v-list v-else v-for="(task, index) in sortTasks" :key="index">
          <v-list-item>
            <template v-slot:prepend>
              <v-list-item-action start>
                <v-checkbox-btn v-model="task.completed"/>
              </v-list-item-action>
            </template>

            <v-list-item-title :class="{'done': task.completed}">
              {{ task.title }}
            </v-list-item-title>

            <v-list-item-subtitle>
              Créé le {{ new Date(task.date).toLocaleDateString() }}
              à {{ new Date(task.date).toLocaleTimeString() }}
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
import {computed, ref, watch} from 'vue';

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
const newTask = ref("");

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

// Trier les tâches par date de création (du plus récent au plus ancien)
const sortTasks = computed(() => {
  return tasks.value.slice().sort((a, b) => b.date - a.date);
});

// Supprimer la liste si "delete" est inscrit dans le champ de saisie
watch(newTask, (value) => {
  if (value.toLowerCase() === "delete") {
    tasks.value = [];
    newTask.value = "";
  }
});
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
