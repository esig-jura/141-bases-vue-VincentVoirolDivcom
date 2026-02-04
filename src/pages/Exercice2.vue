<template>
  <v-container max-width="700">
    <!-- Donnée de l'exercice -->
    <exercice-objectifs number="2" />
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>

      <!-- Formulaire pour modifier les données -->
      <v-form class="my-6">
        <!-- Ajoutez ici une liaison dynamique avec la variable title -->
        <v-text-field
          label="Modifier le titre"
          placeholder="Entrez un nouveau titre"
          outlined
          class="mb-4"
        />
        <!-- Ajoutez ici une liaison dynamique avec la variable description -->
        <v-textarea
          label="Modifier la description"
          placeholder="Entrez une nouvelle description"
          outlined
          rows="3"
        />
      </v-form>

      <!-- Carte dynamique -->
      <v-card class="mx-auto my-6 pa-2" max-width="400">
        <!-- Titre dynamique -->
        <v-card-title>*** TITRE ***</v-card-title>

        <!-- Description dynamique -->
        <v-card-subtitle>
          *** DESCRIPTION ***
        </v-card-subtitle>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
// Importation du composant contenant la donnée de l'exercice
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";

// Données préparées pour l'exercice
const title = "Bienvenue à l'exercice 2"
const description = "Cet exercice teste la gestion des événements et l'interaction avec les formulaires."
</script>

