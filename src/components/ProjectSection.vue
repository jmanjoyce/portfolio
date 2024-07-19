<template>
    <v-container>
        <v-row justify="center">
            <v-col cols="12" class="text-center">
                <h1 class="display-1">Projects</h1>
            </v-col>
        </v-row>
        <v-row justify="center">
            <v-col
                v-for="(experience) in experiences"
                :key="experience.title"
                cols="12"
                sm="8"
                md="6"
                lg="4"
            >
                <v-hover v-slot="{ isHovering, props }">
                    <v-card
                        v-bind="props"
                        :image="experience.image"
                        color="surface-variant"
                        hover
                        ref="cards"
                    >
                        <div class="title-overlay" v-show="!isHovering">
                            <v-card-title>{{ experience.title }}</v-card-title>
                        </div>
                        <div :class="[isHovering ? '' : 'hide']">
                            <!-- <v-card-title class="title-overlay">{{ experience.title }}</v-card-title> -->
                            <v-card-text class="text-overlay">
                                {{ experience.description }}
                            </v-card-text>
                            <v-card-actions class="justify-center">
                                <v-btn
                                    text="View Source"
                                    :href="experience.source"
                                    target="_blank"
                                    size="small"
                                    variant="elevated"
                                    color="blue-lighten-2"
                                    block
                                ></v-btn>
                            </v-card-actions>
                        </div>
                    </v-card>
                </v-hover>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import { defineComponent, Ref, ref } from "vue";

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
        cardHeights: number[];
        cards: Ref<HTMLDivElement[]>;
    } {
        return {
            experiences: [
                
                {
                    title: "Catan Reasources Bot",
                    description:
                        "Developed a Chrome extension to track resource cards in the online Catan platform, Colonist.io. The extension leverages Chrome's local storage to monitor DOM mutations, using threads to efficiently process and parse DOM content. This allows players to keep track of other players' resources in real-time. The extension features a user-friendly interface within the Chrome extension dropdown, displaying comprehensive resource information for each player.",
                    source: "https://github.com/jmanjoyce/catan-tracking-extension",
                    image: require("@/assets/catan.jpg"),
                    keyFeatures: [],
                },
                {
                    title: "Real-Estate Blockchain",
                    description:
                        "Developed a real-estate blockchain network deployed on AWS EC2 nodes. This network enables users to buy properties on the blockchain, akin to purchasing bitcoins, ensuring transparency and security in real estate transactions. The system implements a robust proof-of-work mining algorithm with consensus synchronization for reliable transaction validation. The project is an end-to-end JavaScript application utilizing Vue.js for the frontend, Node.js and Express.js for the backend, and MongoDB for the database. Mongoose is employed as an ORM for efficient querying across the blockchain network, ensuring seamless data management and retrieval.",
                    source: "https://github.com/jmanjoyce/real-estate-blockchain",
                    image: require("@/assets/blockchain.jpg"),
                    keyFeatures: [
                        "Blockchain-based property transactions",
                        "Proof-of-work mining algorithm",
                        "Consensus synchronization for transaction validation",
                        "Deployed on AWS EC2 nodes with docker images",
                        "Comprehensive tech stack: Vue.js, Node.js, Express.js, MongoDB",
                    ],
                },
                {
                    title: "Snowpack Visualization Tool",
                    description:
                        "Developed an interactive JavaScript visualization tool designed for searching through and analyzing snowpack data. Initially created for the Mount Washington Avalanche Center, this tool utilizes D3.js to present snowpack time series data spanning multiple years. It aids researchers in understanding snowpack patterns and the impacts of climate change, enhancing avalanche forecasting accuracy.",
                    source: "https://github.com/jmanjoyce/snowpack-vis",
                    image: require("@/assets/cannon.jpg"),
                    keyFeatures: [],
                },
            ],
            cardHeights: [],
            cards: ref([]),
        };
    },
    mounted() {
        this.calculateHeights();
        console.log(this.cardHeights);
        window.addEventListener("resize", this.calculateHeights);
    },
    beforeUnmount() {
        window.removeEventListener("resize", this.calculateHeights);
    },
    methods: {
        calculateHeights() {
            this.cardHeights = this.cards.map((card: any) => {
                const cardTitle = card.querySelector(".v-card-title");
                const cardText = card.querySelector(".text-overlay");
                const cardActions = card.querySelector(".v-card-actions");
                console.log(
                    Math.max(
                        cardTitle.offsetHeight,
                        cardText.offsetHeight + cardActions.offsetHeight
                    )
                );
                return Math.max(
                    cardTitle.offsetHeight,
                    cardText.offsetHeight + cardActions.offsetHeight
                );
            });
        },
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
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 8px;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1;
    transition: opacity 0.3s, visibility 0.3s;
}

.text-overlay {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    padding: 16px;
    flex-grow: 1;
    /* //height: 70%; */
}

.hide {
    visibility: hidden;
}
</style>
