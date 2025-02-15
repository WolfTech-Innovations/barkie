<template>
  <div class="h-screen grid grid-cols-3 divide-x bg-gray-900 text-white">
    <div class="col-span-2 h-screen flex flex-col bg-gray-800">
      <div class="flex-1 overflow-y-auto p-8">
        <!-- Branding Header -->
        <div class="mb-6">
          <h1 class="text-3xl font-semibold">Barkie</h1>
          <p class="text-sm text-gray-400">by WolfTech Innovations</p>
        </div>

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
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700 mt-4 hover:bg-slate-200"
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

<style scoped>
/* Dark Mode Adjustments */
.bg-gray-900 {
  background-color: #111827;
}

.bg-gray-800 {
  background-color: #1f2937;
}

.text-white {
  color: white;
}

.text-gray-400 {
  color: #9ca3af;
}

.text-slate-700 {
  color: #4b5563;
}

.hover\:bg-slate-200:hover {
  background-color: #e5e7eb;
}

button {
  border-color: #374151;
}
</style>
