<template>
  <header class="flex justify-center items-center bg-[#171738] h-12">
    <router-link to="/">
      <div class="flex">
        <h1
          class="text-[#FFD9CE] tracking-widest text-2xl font-semibold after:content-['images'] after:text-xs after:italic after:tracking-tight"
        >
          NASA
        </h1>
      </div>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>
