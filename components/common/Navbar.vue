<template>
    <nav class="flex justify-center">
      <div class="px-8 py-2.5 mt-[5px] bg-gradient-to-r from-amber-500/30 to-blue-900/30 backdrop-blur-md rounded-lg flex items-center" >
        <div class="hidden md:flex items-center space-x-8">
          <NuxtLink to="/" class="text-white hover:text-gray-300 transition-colors">Home</NuxtLink>
          <div class="text-white">|</div>
          <NuxtLink to="/links" class="text-white hover:text-gray-300 transition-colors">Links</NuxtLink>
          <div class="text-white">|</div>
          <NuxtLink to="/about" class="text-white hover:text-gray-300 transition-colors">About</NuxtLink>
        </div>
        <UButton
          variant="ghost" 
          color="white"
          class="md:hidden absolute right-4"
          icon="i-heroicons-bars-3"
        />
      </div>
    </nav>
</template>