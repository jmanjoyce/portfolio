<template>
<div>
    <v-app>
    <div>
        <HeaderSec></HeaderSec>
    </div>
    <v-main class="no-padding">
    <div>
       <TitleSection id="home"></TitleSection>
    </div>

    <div>
        <v-container>
        <AboutSec id="about"></AboutSec>
        </v-container>
    </div>
    <div>
        <ExperienceSec id="experience"></ExperienceSec>
    </div>
    <div>
        <ProjectSection id="projects"></ProjectSection>
    </div>
    <div>
        <FooterBottom id="contact"></FooterBottom>
    </div>
    </v-main>
    </v-app>
   
    
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AboutSec from '../components/AboutSec.vue'
import FooterBottom from '../components/FooterBottom.vue'
import HeaderSec from '../components/HeaderSec.vue'
import ProjectSection from '../components/ProjectSection.vue'
import ExperienceSec from '../components/ExperienceSec.vue'
import TitleSection from '../components/TitleSection.vue'

export default defineComponent({
    name: "PortfolioPage",
    components: { AboutSec, FooterBottom, HeaderSec, ProjectSection, ExperienceSec, TitleSection},
   
})

</script>

<style>

/* Remove default padding and margin for the body */
body {
  margin: 0;
  padding: 0;
}

.no-padding {
  padding: 0 !important;
}

/* Ensure v-main takes full height */
v-main {
  min-height: 100vh;
}

</style>