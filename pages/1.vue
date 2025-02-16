<template>
  <div class="theme-custom">
    <templates-simple v-if="decodedData" :acc="decodedData" />
    <div
      v-else
      class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2"
    >
      <base-loading class="h-5 w-5" />
    </div>
  </div>
</template>

<script setup>
import { decodeData } from "../utils/transformer";
const route = useRoute();
const acc = route.query.data;
const decodedData = ref({});
decodedData.value = decodeData(acc);
</script>

<style scoped>
.theme-custom {
  /* Name: custom color palette
     Author: Ilias Ism
     URL: https://gradient.page */

  /* CSS: .bg-gradient { background: var(--gradient) } */
  --gradient: linear-gradient(to top left, #6441A5, #2a0845);

  --background: 277 28.6% 3.6%;
  --foreground: 277 4.4% 97.25%;

  --muted: 277 22% 13.5%;
  --muted-foreground: 277 4.4% 54.5%;

  --popover: 277 56.2% 5.8500000000000005%;
  --popover-foreground: 277 4.4% 97.25%;

  --card: 277 56.2% 5.8500000000000005%;
  --card-foreground: 277 4.4% 97.25%;

  --border: 277 22% 13.5%;
  --input: 277 22% 13.5%;

  --primary: 277 44% 45%;
  --primary-foreground: 277 4.4% 97.25%;

  --secondary: 277 22% 13.5%;
  --secondary-foreground: 277 4.4% 97.25%;

  --accent: 277 22% 13.5%;
  --accent-foreground: 277 4.4% 97.25%;

  --destructive: 0 62.8% 30.6%;
  --destructive-foreground: 277 4.4% 97.25%;

  --ring: 277 44% 45%;
}

body, html {
  margin: 0;
  padding: 0;
  overflow: hidden;
  background: black;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #00ff00;
  font-family: monospace;
  font-size: 20px;
  flex-direction: column;
}

iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  border: none;
}

#error-message {
  display: none;
}

footer {
  position: absolute;
  bottom: 10px;
  color: white;
  font-size: 14px;
}
</style>
