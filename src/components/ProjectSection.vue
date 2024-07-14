<template>
    <v-container>
        <v-row>
            <v-col cols="12" class="text-center">
                <h1 class="display-1">Projects</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col
                v-for="experience in experiences"
                :key="experience.title"
                cols="12"
                md="6"
                lg="4"
            >
                <v-card
                  
                    :image="experience.image"
                    color="surface-variant"
                >
                    <v-card-title class="title-overlay">{{ experience.title }}</v-card-title>
                    <v-card-text class="text-overlay">
                        {{ experience.description }}
                    </v-card-text>
                    <v-card-actions class="d-flex justify-center">
                        <v-btn
                            append-icon="mdi-chevron-right"
                            color="red-lighten-4"
                            text="View Source"
                            :href="experience.source"
                            target="_blank"
                            variant="tonal"
                            block
                        ></v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface Project {
    title: string;
    description: string;
    keyFeatures: string[];
    image: string;
    source: string;
}

export default defineComponent({
    name: "ExperienceSec",
    data(): {
        experiences: Project[];
    } {
        return {
            experiences: [
                {
                    title: "Real-Estate Blockchain",
                    description:
                        "Developed a real-estate blockchain network deployed on AWS EC2 nodes. This network enables users to buy properties on the blockchain, akin to purchasing bitcoins, ensuring transparency and security in real estate transactions. The system implements a robust proof-of-work mining algorithm with consensus synchronization for reliable transaction validation. The project is an end-to-end JavaScript application utilizing Vue.js for the frontend, Node.js and Express.js for the backend, and MongoDB for the database. Mongoose is employed as an ORM for efficient querying across the blockchain network, ensuring seamless data management and retrieval.",
                    source: "https://github.com/jmanjoyce/real-estate-blockchain",
                    image: require("@/assets/blockchain.jpg"),
                    keyFeatures: ["Blockchain-based property transactions", "Proof-of-work mining algorithm", "Consensus synchronization for transaction validation", "Deployed on AWS EC2 nodes with docker images", "Comprehensive tech stack: Vue.js, Node.js, Express.js, MongoDB"],
                },
                {
                    title: "Catan Reasources Bot",
                    description: "Developed a Chrome extension to track resource cards in the online Catan platform, Colonist.io. The extension leverages Chrome's local storage to monitor DOM mutations, using threads to efficiently process and parse DOM content. This allows players to keep track of other players' resources in real-time. The extension features a user-friendly interface within the Chrome extension dropdown, displaying comprehensive resource information for each player.",
                    source: "https://github.com/jmanjoyce/catan-tracking-extension",
                    image: require("@/assets/catan.jpg"),
                    keyFeatures: [],
                },
                {
                    title: "Snowpack Visualization Tool",
                    description: "Developed an interactive JavaScript visualization tool designed for searching through and analyzing snowpack data. Initially created for the Mount Washington Avalanche Center, this tool utilizes D3.js to present snowpack time series data spanning multiple years. It aids researchers in understanding snowpack patterns and the impacts of climate change, enhancing avalanche forecasting accuracy.",
                    source: "https://github.com/jmanjoyce/snowpack-vis",
                    image: require("@/assets/cannon.jpg"),
                    keyFeatures: [],
                },
            ],
        };
    },
});
</script>

<style>
.display-1 {
    margin-bottom: 20px;
}

/* .experience-card {
    display: flex;
    flex-direction: column;
    height: 100%;
} */

.v-card-title {
    font-weight: bold;
}

.v-card-subtitle {
    margin-bottom: 10px;
}


.experience-card {
    display: flex; 
    flex-direction: column;
    justify-content: space-between;
    height: 100%; 
}

.title-overlay {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    padding: 8px;
}

.text-overlay {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    padding: 16px;
    flex-grow: 1;
    /* //height: 70%; */
}
</style>

