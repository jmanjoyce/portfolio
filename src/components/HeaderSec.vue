
<template>
  <v-app-bar app>
        <v-toolbar-title>Jared Joyce</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn href="#home">Home</v-btn>
        <v-btn href="#about">About</v-btn>
        <v-btn href="#experience">Experience</v-btn>
        <v-btn href="#projects">Projets</v-btn>
        <v-btn href="#contact">Contact</v-btn>
    </v-app-bar>
   
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "HeaderSec",

})

</script>
