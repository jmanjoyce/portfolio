
<template>
  <v-app-bar app>
        <v-toolbar-title href="#home">
          Jared Joyce
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <!-- <v-btn d-none d-md-flex href="#home">Home</v-btn> -->
        <v-btn d-none d-md-flex href="#about">About</v-btn>
        <v-btn d-none d-md-flex href="#experience">Experience</v-btn>
        <v-btn d-none d-md-flex href="#projects">Projets</v-btn>
        <v-btn d-none d-md-flex href="#contact">Contact</v-btn>
    </v-app-bar>
   
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "HeaderSec",

})

</script>
