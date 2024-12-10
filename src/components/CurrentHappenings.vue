<template>
    <v-container>
        <v-row>
            <v-col cols="12" class="text-center">
                <h1 class="display-1">What I'm Currently up to, Quasp!!</h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-card>
                 
                    <v-card-text class="d-flex about-content">
                        <div class="about-text">
                            
                            <p class="text">
                                Quasp is an App that encourages users to travel and explore the world by collecting tokens as an incentive. The idea for the app came out of an interest in finding a better way to show proof of achievement when it came to hiking and mountaineering. The original idea was to provide hikers a way to prove they hiked a certain mountain or completed a certain hiking list (like all the Colorado 14ers) as opposed to the original method of just writing in a pen and paper that you went somewhere. The solution was to leverage blockchain technology and anti-gps-spoofing machine learning techniques to create soul-bound NFTs that were awarded to users when they achieved a geographic location. The applications for Quasp are endless! From restaurants, tourism, country stamps, mountaineering, and many, many more! 

                            </p>
                            <p class="text">
                                The MVP for the app is built using react native and is connected to a Mongo/Express backend. I’m using Polygon/Ethereum to deploy solidity smart contracts for on-chain operations such as minting new NFTs and inputting which wallets are allowed to mint which NFTs. I’m conducting location verification on off-chain APIs to reduce the gas costs that using on-chain oracles would lead to. As I continue to build a more comprehensive and usable app I’m looking towards using Unity to create a better augmented reality experience on the app. One that is better than that of Pokemon Go. I hope to have a Beta version for people to begin using by February 2025 and make it available on the App stores by May 2025.

                            </p>
                           
                        </div>
                        <v-img
                            class="about-image"
                            :src="require('@/assets/quasp.png')"
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
    name: "CurrentHappenings",
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
