<template>
  <nav class="flex items-center justify-between flex-wrap bg-primaryColor p-6">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
      <span class="font-semibold text-xl tracking-tight">{{ appName }}</span>
    </div>
    <div class="block lg:hidden">
      <button @click="appMenu.visible = !appMenu.visible" class="flex items-center px-3 py-2 border rounded text-white hover:text-white hover:border-white">
        <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path class="fill-white" d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
      </button>
    </div>
    <div v-if="appMenu.visible" class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
      <div class="text-sm lg:flex-grow">
        <a v-for="feature in features" v-if="feature.available" href="#responsive-header" class="block mt-4 lg:inline-block lg:mt-0 text-white hover:text-white mr-4">
          {{ feature.text }}
        </a>
      </div>
      <div>
        <a :href="cta.link" target="_blank" class="inline-block text-sm px-4 py-2 leading-none border rounded text-white border-white hover:border-transparent hover:text-primaryColor hover:bg-white mt-4 lg:mt-0">{{ cta.text }}</a>
      </div>
    </div>
  </nav>
</template>

<script>
import Logo from '~/components/Logo.vue'
import appConfig from '../appConfig.js'

const details = appConfig.details

export default {
  components: {
    Logo
  },
  data() {
    return {
      appName: details.appName,
      appMenu: {
        visible: true
      },
      cta: {
        text: details.cta.text,
        link: details.cta.link
      },
      features: appConfig.features
    }
  }
}
</script>