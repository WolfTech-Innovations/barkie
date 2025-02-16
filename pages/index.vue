<template>
  <div class="h-screen grid grid-cols-1 md:grid-cols-3 divide-x theme-custom">
    <div class="col-span-1 md:col-span-2 h-screen flex flex-col bg-slate-100">
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
<script type="text/javascript" src="js/materialize.min.js"></script>
<style src="https://cdn.jsdelivr.net/npm/@materializecss/materialize@2.2.0/dist/css/materialize.min.css"></style>
</template>
