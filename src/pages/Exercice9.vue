<template>
  <v-container max-width="700">
    <!-- Données de l'exercice -->
    <exercice-objectifs number="9"/>
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <carte-avec-slots v-for="item in items" :key="item.id">
        <template #header>
          {{ item.header }}
        </template>
          {{ item.content }}
        <template #footer>
          <v-btn color="primary">{{ item.footer }}</v-btn>
        </template>
      </carte-avec-slots>

    </div>
  </v-container>
</template>

<script setup>
// Importation des données de l'exercice
import ExerciceObjectifs from "@/components/ExerciceObjectifs.vue";
import CarteAvecSlots from "@/components/CarteAvecSlots.vue";
// Importer les méthodes de vue
const items = [
  { id: 1, header: "EMT", content: "Cité des Microtechniques - Porrentruy", footer: "S'inscrire à l'EMT" },
  { id: 2, header: "ESIG", content: "Rue de l'Avenir 33a - Delémont", footer: "S'inscrire à l'ESIG" },
  { id: 3, header: "HEG", content: "Espace de l'Europe 20 - Neuchâtel", footer: "S'inscrire à la HEG" }
];

</script>

<style scoped lang="sass">

</style>
