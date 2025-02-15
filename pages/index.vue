<template>
  <div class="h-screen grid grid-cols-3 divide-x">
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
