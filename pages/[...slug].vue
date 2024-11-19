<template>
    <div id="blog-page" class="min-h-screen w-screen flex items-center justify-center relative overflow-hidden">
      <div id="blog-page-content" class="flex items-center justify-center w-full max-w-4xl mx-auto px-4 md:px-8 lg:px-12 my-[50px]">
        <FeaturesWaitlistContentContainer 
            class="w-full flex items-start justify-start" 
            id="blog-page-content-container"
        >
          <ContentDoc class="text-black text-center p-10 rounded-xl max-w-4xl markdown-body bg-transparent" />
        </FeaturesWaitlistContentContainer>
      </div>
    </div>
</template>