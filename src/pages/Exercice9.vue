<template>
  <v-container max-width="700">
    <!-- Données de l'exercice -->
    <exercice-objectifs number="9"/>
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <!-- À faire : utiliser un composant, des slots et afficher dynamiquement les items du tableau -->
      <v-card class="card" v-for="item in items" :key="item.id">
        <v-card-title>
          <strong>
            <CarteAvecSlots>
              {{ item.header }}
            </CarteAvecSlots>
          </strong>
        </v-card-title>
        <v-card-text>
          {{ item.content }}
        </v-card-text>
        <v-card-actions>
          <v-btn color="primary">{{ item.footer }}</v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
// Importation des données de l'exercice
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";
import CarteAvecSlots from "@/components/CarteAvecSlots.vue";

// Données préparées pour l'exercice
// eslint-disable-next-line no-unused-vars <-- cette ligne empêche l'erreur de variable non utilisée
const items = [
  { id: 1, header: "EMT", content: "Cité des Microtechniques - Porrentruy", footer: "S'inscrire à l'EMT" },
  { id: 2, header: "ESIG", content: "Rue de l'Avenir 33a - Delémont", footer: "S'inscrire à l'ESIG" },
  { id: 3, header: "HEG", content: "Espace de l'Europe 20 - Neuchâtel", footer: "S'inscrire à la HEG" }
];

</script>

<style scoped>
.card {
  margin-bottom: 20px;
}
</style>
