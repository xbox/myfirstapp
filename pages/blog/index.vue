<template>
    <div class="min-h-screen w-screen flex flex-col items-center justify-center relative overflow-hidden" style="background-image: url('/pascal.jpg'); background-size: cover; background-position: center; background-repeat: no-repeat;">
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center w-full px-4 md:px-8 lg:px-12">
        <FeaturesWaitlistContentContainer>
          <ContentDoc class="text-white text-center m-10" />
          <div class="w-full max-w-2xl mx-auto mt-8">
            <h1 class="text-3xl font-bold text-white mb-6 text-center">博客文章列表</h1>
            <div class="space-y-4">
                <ContentList path="/blog">
                    <template #default="{ list }">
                        <div class="space-y-4">
                            <div v-for="article in list" :key="article._path" class="bg-white/20 backdrop-blur-md rounded-lg p-4 hover:bg-white/30 transition-all duration-300">
                                <NuxtLink :to="article._path" class="block">
                                    <h2 class="text-xl font-semibold text-white mb-2">{{ article.title }}</h2>
                                    <p class="text-white/80 text-sm">{{ article.description || '阅读更多' }}</p>
                                    <div class="text-white/60 text-xs mt-2">{{ article.date }}</div>
                                </NuxtLink>
                            </div>
                        </div>
                    </template>
                </ContentList>
          </div>
          </div>
        </FeaturesWaitlistContentContainer>
      </div>
    </div>
</template>