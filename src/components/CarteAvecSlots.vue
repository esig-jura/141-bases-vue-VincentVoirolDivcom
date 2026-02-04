<script setup>

</script>

<template>
  <v-card style="margin-bottom:20px;">
    <v-card-title>
      <slot name="header">En-tête par défaut</slot>
    </v-card-title>
    <v-card-text>
      <slot>Contenu principal par défaut</slot>
    </v-card-text>
    <v-card-actions>
      <slot name="footer">Pied de carte par défaut</slot>
    </v-card-actions>
  </v-card>
</template>

