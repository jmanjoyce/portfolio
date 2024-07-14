<template>
    <v-container>
        <v-row>
            <v-col>
                <v-card>
                    <v-card-title> About Me </v-card-title>
                    <v-card-text class="d-flex about-content">
                        <div class="about-text">
                            <p class="text">
                                Hi, I'm Jared. I recently graduated from Bowdoin College, where I double majored in Mathematics and Computer Science, and minored in English. During my time at Bowdoin, I was a dedicated member of the track team, specializing in the 400m.
                                I broke two school records and secured numerous top-three finishes in both the individual 400m and the 4x400m relay at the NESCAC championships. 
                            </p>
                            <p class="text">
                                Beyond my academic and athletic pursuits, I have a deep passion for software engineering, I have loved the work I have done in networking and crypto as well as in data visualization but I am open to most rolls. In my free time, I enjoy climbing which I take too seriously, backcountry skiing which helps me see the world and reading which keeps me young.
                            </p>
                        </div>
                        <v-img
                            class="about-image"
                            :src="require('@/assets/ski_france.jpg')"
                            alt="About Image"
                            max-width="300"
                        ></v-img>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "AboutSec",
});
</script>

<style scoped>
.about-content {
    align-items: center;
}

.about-text {
    flex: 70%;
}

.text {
    font-size: 1.2rem;
    line-height: 1.6;
    margin-bottom: 1rem;
}

.about-image {
    flex: 30%;
    flex-shrink: 0;
    margin-left: 20px;
}
</style>
