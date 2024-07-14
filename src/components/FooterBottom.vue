<template>
    <div>
        <v-footer
      color="primary"
      class="footer"
    >
      <v-container>
        <v-row>
          <v-col
            cols="12"
            class="text-center"
          >
            <h2 class="footer-title">Contact Me</h2>
            <p class="footer-info">Email: jmanjoyce@gmail.com</p>
            <p class="footer-info">Phone: +1 (508) 244-2757</p>
            <div class="footer-info">
              <v-icon class="mr-2">mdi-linkedin</v-icon>
              <a href="https://www.linkedin.com/in/jared-joyce-a09615201/" target="_blank">LinkedIn</a>
            </div>
            <div class="footer-info">
              <v-icon class="mr-2">mdi-github</v-icon>
              <a href="https://github.com/jmanjoyce" target="_blank">GitHub</a>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>
      </div>
</template>

   


<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "FooterBottom",

})
</script>

<style>
.footer {
  padding: 20px 0;
  color: white;
  position: relative;
  bottom: 0;
  width: 100%;
  z-index: 1000;
}

.footer-title {
  margin-bottom: 10px;
}

.footer-info {
  margin: 5px 0;
  display: flex;
  align-items: center;
}

.footer-info a {
  color: white;
  text-decoration: none;
}

.footer-info a:hover {
  text-decoration: underline;
}
</style>