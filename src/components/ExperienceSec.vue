<template>
    <v-container>
        <v-row>
            <v-col cols="12" class="text-center">
                <h1 class="display-1">Work Experience</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col
                v-for="experience in experiences"
                :key="experience.company"
                cols="12"
                md="6"
                lg="4"
            >
                <v-card class="experience-card">
                    <v-card-title>
                        <div>
                            <h3>{{ experience.company }}</h3>
                        </div></v-card-title
                    >
                    <v-card-text>
                        <p class="subtitle-2">{{ experience.title }}</p>
                        <p class="subtitle-2">{{ experience.date }}</p>
                        <div class="spacer"></div>

                        <ul>
                            <li
                                v-for="(desc, i) in experience.description"
                                :key="i"
                            >
                                {{ desc }}
                            </li>
                        </ul>
                        <div v-if="experience.skills">
                            <p>
                                <strong>Skills:</strong>
                                {{ experience.skills }}
                            </p>
                        </div>

                        <div v-if="experience.secondTitle" class="spacer"></div>

                        <p v-if="experience.secondTitle" class="subtitle-2">
                            {{ experience.secondTitle }}
                        </p>
                        
                        <p v-if="experience.secondDate" class="subtitle-2">
                            {{ experience.secondDate }}
                        </p>
                        <div v-if="experience.secondTitle" class="spacer"></div>

                        <div v-if="experience.secondDescription">
                            <ul>
                                <li
                                    v-for="(
                                        desc, i
                                    ) in experience.secondDescription"
                                    :key="i"
                                >
                                    {{ desc }}
                                </li>
                            </ul>
                        </div>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface Experience {
    company: string;
    title: string;
    date: string;
    description: string[];
    skills?: string;
    secondTitle?: string;
    secondDate?: string;
    secondDescription?: string[];
}

export default defineComponent({
    name: "ExperienceSec",
    data(): {
        experiences: Experience[];
    } {
        return {
            experiences: [
                {
                    company: "UbiSoft",
                    title: "NLP Software Engineer",
                    date: "May 2023 - August 2023",
                    description: [
                        "Developed a data annotation platform from the ground up, leveraging Vue.js, SCSS, TypeScript, and MongoDB, improving NLP training data by streamlining the annotation process and enhancing data quality.",
                        "Utilized GPT-4 for knowledge distillation to train smaller domain-specific summarization models for video game scripts and stories.",
                        "Created intuitive visualization tools using D3.js and Vue.js to visualize character franchise information for writers to use as a reference for continuing franchises.",
                    ],
                    skills: " Vue.js, Typescript, Python, MongoDB, SCSS",
                },
                {
                    company: "Idexx",
                    title: "Full-Software Enginner",
                    date: "May 2022 - January 2023",
                    description: [
                        "Contributed to a Full Stack Agile (scrum) development team constructing applications using PostgresDB, Express.js, Nest.js, Node, and React hosted on AWS.",
                        "Enhanced backend search using AWS OpenSearch, resulting in a 92% percent decrease in runtime.",
                        "Leveraged AWS serverless architecture to build a throttled queueing system using SNS, and SQS.",
                    ],
                    skills: "React, Express.js, Nest.js, TypeScript, PostgreSQL, AWS serverless, Cypress",
                },
                {
                    company: "Bowdoin College",
                    title: "Computer Science Research Fellow",
                    date: "May 2021 - May 2023",
                    description: [
                        "Employed Game-Theoretic Approaches to model and understand networked systems of influence in the context of voting behavior and patterns.",
                        "Implemented BackJumping and Constraint Learning algorithms in C++ optimized for Influence games networks.",
                    ],
                    secondTitle: "Computer Science and Math Learning Assistant",
                    secondDate: "September 2021 - May 2024",
                    secondDescription: [
                        "Assisted students through CSCI 2200 Algorithms, CSCI 2320 Principles of Programming languages, CSCI 2303 Systems, and MATH 2600 Statistics.",
                        "Guided students through learning difficult concepts, and provided constructive, positive feedback in a timely manner.",
                    ],
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

.experience-card {
    height: 100%;
}

.experience-card h3 {
    margin: 0;
}



.experience-card ul {
    text-align: left;
}

.experience-card .subtitle-2 {
    margin: 0;
    color: gray;
}

.v-card-title {
    flex-direction: column;
    align-items: flex-start;
}

.v-card-title > div {
    width: 100%;
}

.v-card-text ul {
    padding-left: 20px; /* Adjust padding to suit your design */
    list-style-type: disc; /* Change to a different style if needed */
}

.v-card-text ul li {
    margin-bottom: 10px;
}

.spacer {
    margin-top: 10px;
}
</style>
