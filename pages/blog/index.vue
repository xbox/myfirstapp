<template>
    <div class="min-h-screen w-screen flex flex-col items-center justify-center relative overflow-hidden" style="background-image: url('/pascal.jpg'); background-size: cover; background-position: center; background-repeat: no-repeat;">
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center w-full px-4 md:px-8 lg:px-12">
        <FeaturesWaitlistContentContainer>
          <ContentDoc class="text-white text-center m-10" />
          <div class="w-full max-w-6xl mx-auto mt-8">
            <h1 class="text-3xl font-bold text-white mb-6 text-center">博客文章列表</h1>
            <ContentList path="/blog">
              <template #default="{ list }">
                <div class="grid grid-cols-2 gap-6">
                  <div 
                    v-for="article in list.slice(0, 20)" 
                    :key="article._path" 
                    class="bg-white/20 backdrop-blur-md rounded-lg p-6 hover:bg-white/30 transition-all duration-300 transform hover:-translate-y-2"
                  >
                    <NuxtLink :to="article._path" class="block">
                      <h2 class="text-xl font-bold text-white mb-3">{{ article.title }}</h2>
                      <p class="text-white/80 text-sm mb-4 line-clamp-3">
                        {{ article.description || '暂无描述，点击阅读更多' }}
                      </p>
                      <div class="text-right">
                        <span class="text-white/70 text-sm hover:text-white transition-colors">阅读更多 →</span>
                      </div>
                    </NuxtLink>
                  </div>
                </div>
              </template>
              <template #not-found>
                <div class="text-white/80 text-sm text-center">暂无文章</div>
              </template>
            </ContentList>
          </div>
        </FeaturesWaitlistContentContainer>
      </div>
    </div>
</template>