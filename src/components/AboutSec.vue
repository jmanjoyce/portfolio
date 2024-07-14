<template>
    <v-container>
        <v-row>
            <v-col>
                <v-card>
                    <v-card-title> About Me </v-card-title>
                    <v-card-text class="d-flex">
                        <div class="about-text">
                            <!-- Add your about content here -->
                            <p>
                                Stupid about
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
.about-text {
    flex: 60%;
}

.about-image {
    flex: 40%;

    flex-shrink: 0;
    margin-left: 20px;
}
</style>
