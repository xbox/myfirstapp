<template>
    <div class="min-h-screen w-screen flex flex-col items-center justify-center relative overflow-hidden" style="background-image: url('/pascal.jpg'); background-size: cover; background-position: center; background-repeat: no-repeat;">
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 flex flex-col items-center w-full px-4 md:px-8 lg:px-12">
          <FeaturesWaitlistLableMini />
          <CommonTitlePrimary />
        <FeaturesWaitlistContentContainer>
          <FeaturesWaitlistContentHeader />
          <FeaturesWaitlistContentDescription />
          <FeaturesWaitlistContentJoinButton />
        </FeaturesWaitlistContentContainer>
          <CommonSocialLinks />
      </div>
    </div>
</template>
<script setup></script>