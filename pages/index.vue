<template>
  <div class="h-screen grid grid-cols-3 divide-x theme-custom">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <!-- Centered Branding Header -->
      <div class="py-6 bg-white shadow-md text-center">
        <h1 class="text-4xl font-extrabold text-slate-900">Barkie</h1>
        <p class="text-sm text-slate-500">by WolfTech Innovations</p>
      </div>

      <div class="flex-1 overflow-y-auto p-8">
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
        
        <!-- Publish Button -->
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border border-slate-300 text-xs font-medium bg-white text-slate-700 mt-4 hover:bg-slate-200"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
      </div>
    </div>
  </div>
</template>

<style>
.theme-custom {
    /* Name: custom color palette
       Author: Ilias Ism
       URL: https://gradient.page */

    /* CSS: .bg-gradient { background: var(--gradient) } */
    --gradient: linear-gradient(to top left,#6441A5,#2a0845);

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
</style>

<script setup>
import { ref } from "vue";
import { encodeData } from "../utils/transformer";

const data = ref({
  n: "",
  d: "",
  i: "",
  f: "",
  t: "",
  ig: "",
  gh: "",
  tg: "",
  l: "",
  e: "",
  w: "",
  y: "",
  ls: [],
});

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};
</script>
<script>
export default {
  mounted() {
    // Dynamically add the AdSense script for Auto Ads
    const script = document.createElement("script");
    script.src = "https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-8933145913893262";
    script.async = true;
    script.crossOrigin = "anonymous";
    document.head.appendChild(script);

    // Optional: Initialize Auto Ads (Google handles this automatically, but this is for completion)
    script.onload = () => {
      (window.adsbygoogle = window.adsbygoogle || []).push({});
    };
  }
};
</script>
