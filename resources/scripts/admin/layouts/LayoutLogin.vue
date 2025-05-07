<template>
  <div class="grid h-screen grid-cols-12 overflow-y-auto bg-gray-100">
    <NotificationRoot />

    <div
      class="
        flex
        items-center
        justify-center
        w-full
        col-span-12
        p-4
        mx-auto
        text-gray-900
        sm:p-6
        md:p-8 md:col-span-6
        lg:col-span-5
        flex-2
        py-8
        sm:py-12
        md:py-16
      "
    >
      <div class="w-full max-w-md">
        <MainLogo
          v-if="!loginPageLogo"
          class="block w-36 sm:w-40 md:w-48 h-auto max-w-full mx-auto mb-10 sm:mb-16 md:mb-20 text-primary-500"
        />

        <img
          v-else
          :src="loginPageLogo"
          class="block w-36 sm:w-40 md:w-48 h-auto max-w-full mx-auto mb-10 sm:mb-16 md:mb-20 text-primary-500"
        />

        <router-view />

        <div
          class="
            pt-8
            sm:pt-12
            md:pt-16
            mt-0
            text-xs
            sm:text-sm
            not-italic
            font-medium
            leading-relaxed
            text-center
            text-gray-400
          "
        >
          <p class="mb-3">
            {{ copyrightText }}
            {{ new Date().getFullYear() }}
          </p>
        </div>
      </div>
    </div>
    <div
      class="
        relative
        flex-col
        items-center
        justify-center
        hidden
        w-full
        h-full
        bg-no-repeat bg-cover
        md:col-span-6
        lg:col-span-7
        md:flex
        overflow-hidden
      "
      style="background-image: url('/img_login.jpg'); background-size: cover; background-position: center center;"
    >
      <div class="relative z-50 w-full max-w-lg px-6 md:px-10 lg:px-16">
        <h1
          class="
            hidden
            mb-3
            text-2xl
            sm:text-3xl
            lg:text-4xl
            xl:text-5xl
            font-bold
            leading-tight
            text-center md:text-left
            text-white
            lg:block
          "
        >
          {{ pageHeading }}
        </h1>
        <p
          class="
            hidden
            text-sm
            md:text-base
            not-italic
            font-normal
            leading-relaxed
            text-center md:text-left
            text-gray-100
            lg:block
          "
        >
          {{ pageDescription }}
        </p>
      </div>
      <!-- Overlay oscuro para mejor legibilidad del texto -->
      <div class="absolute inset-0 bg-black bg-opacity-30 z-10"></div>
    </div>
  </div>
</template>

<script setup>
import NotificationRoot from '@/scripts/components/notifications/NotificationRoot.vue'
import MainLogo from '@/scripts/components/icons/MainLogo.vue'
import LoginBackground from '@/scripts/components/svg/LoginBackground.vue'
import LoginPlanetCrater from '@/scripts/components/svg/LoginPlanetCrater.vue'
import LoginBottomVector from '@/scripts/components/svg/LoginBottomVector.vue'
import LoginBackgroundOverlay from '@/scripts/components/svg/LoginBackgroundOverlay.vue'
import { computed, ref } from 'vue'

const pageHeading = computed(() => {
  if (window.login_page_heading) {
    return window.login_page_heading
  }

  return ''
})

const pageDescription = computed(() => {
  if (window.login_page_description) {
    return window.login_page_description
  }

  return ''
})

const copyrightText = computed(() => {
  if (window.copyright_text) {
    return window.copyright_text
  }
  return 'Copyright @ IDEOLOGIX MEDIA DOOEL.'
})

const loginPageLogo = computed(() => {
  if (window.login_page_logo) {
    return window.login_page_logo
  }

  return false
})
</script>

<style lang="scss" scoped>
@media (max-height: 700px) {
  .mb-10 {
    margin-bottom: 1rem !important;
  }
  .py-8 {
    padding-top: 1rem !important;
    padding-bottom: 1rem !important;
  }
  .pt-8 {
    padding-top: 0.5rem !important;
  }
}
</style>
