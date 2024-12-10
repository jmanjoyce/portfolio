<template>
    <v-container   class="title-section" fill-height fluid>
        <v-row  align="center" justify="start">
            <v-col cols="12" class="title-content">
                <div>
                    <GraphOverLay></GraphOverLay>
                </div>
                <div>
                    <h1>Hey, I'm Jared</h1>
                    <p :class="['subtitle-1', 'shadow']">I'm a software engineer</p>
                    <p :class="['subtitle-1', 'shadow']">and I'm currently building Quasp</p>
                </div>
                
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import GraphOverLay from "./GraphOverlay.vue";
export default defineComponent({
    name: "TitleSection",
    components: { GraphOverLay },
});
</script>

<style scoped>
.title-section {
    background: url("@/assets/norway.JPG") no-repeat center center;
    background-size: cover;
    color: white;
    height: 100vh;
    padding: 0; /* Remove any default padding */
}

.shadow {
    text-shadow: -0.5px -0.5px 0 #707070, 0.5px -0.5px 0 #707070, -0.5px 0.5px 0 #707070, 0.5px 0.5px 0 #707070;
}


</style>
