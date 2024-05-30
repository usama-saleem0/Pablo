<script setup>
import { useTheme } from 'vuetify'
import UpgradeToPro from '@/components/UpgradeToPro.vue'
import { hexToRgb } from '@layouts/utils'

const { global } = useTheme()
</script>

<template>
  <VApp class="dashboard-bg" :style="`--v-global-theme-primary: ${hexToRgb(global.current.value.colors.primary)}`">
    <RouterView />
    <!-- <UpgradeToPro /> -->
  </VApp>
</template>


<style scoped>
.dashboard-bg {
  background-color: #0F123BCC;
  background: url(../public/dashboard-bg-img.png) no-repeat top center;
  background-size: cover;
  height: 100%;
  width: 100%;
  position: relative;
}

.dashboard-bg::before {
    position: absolute;
    content: "";
    background: #0F123BCC;
    width: 100%;
    height: 100%;
}


</style>