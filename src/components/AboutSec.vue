<template>
    <v-container>
        <v-row>
            <v-col cols="12" class="text-center">
                <h1 class="display-1">About Me</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-card>
                 
                    <v-card-text class="d-flex about-content">
                        <div class="about-text">
                            <p class="text">
                                Hi, I'm Jared. I recently graduated from Bowdoin College, where I majored in Mathematics and Computer Science and minored in English. As a four-year member of the track team, I broke two school records in the 400M sprint. 


                            </p>
                            <p class="text">
                                I have a deep passion for software engineering, I have had work experience and projects ranging from networking and crypto to data visualization. These experiences have fueled my enthusiasm for creating impactful software solutions that drive data-driven decision-making and secure digital transactions.

                            </p>
                            <p class="text">
                                In my free time, I am an avid sport climber and boulderer. I love the dedication, persistence, and patience climbing requires. It teaches me every day to love the process. Additionally, I love exploring the world through backcountry skiing and learning about it through reading.  

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
.display-1 {
    margin-bottom: 20px;
}
.about-content {
    align-items: center;
}



.about-text {
    flex: 70%;
}

.about-text p {
    text-align: left;
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
