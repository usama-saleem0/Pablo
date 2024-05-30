<script setup>
import { useTheme } from 'vuetify'
import illustrationJohnDark from '@images/cards/illustration-john-dark.png'
import illustrationJohnLight from '@images/cards/illustration-john-light.png'

const { global } = useTheme()
const illustrationJohn = computed(() => global.name.value === 'dark' ? illustrationJohnDark : illustrationJohnLight)


</script>

<template>
  <VCard class="welcomeback-card text-center text-sm-start">
    <VRow no-gutters>
      <VCol
        cols="12"
        sm="8"
        order="2"
        order-sm="1"
      >
        <VCardItem>
          <h5>Welcome Back,</h5>
          <VCardTitle class="text-md-h5 text-white">
            <h3>Mark Johnson</h3>
          </VCardTitle>
        </VCardItem>

        <VCardText>
          <span>
            Glad to see you again!
            <br>
            Ask me anything.
          </span>
          <br>
          <div class="mark-btn">
            <a href="#">Tap to record <i class='bx bx-right-arrow-alt'></i></a>
          </div>
        </VCardText>
      </VCol>

      <!-- <VCol
        cols="12"
        sm="4"
        order="1"
        order-sm="2"
        class="text-center"
      >
        <img
          :src="illustrationJohn"
          :height="$vuetify.display.xs ? '150' : '175'"
          :class="$vuetify.display.xs ? 'mt-6 mb-n2' : 'position-absolute'"
          class="john-illustration flip-in-rtl"
        >
      </VCol> -->
    </VRow>
  </VCard>
</template>

<style lang="css" scoped>


.v-card-item__content h5 {
    font-size: 16px;
    font-family: 'Plus Jakarta Sans';
    color: #A0AEC0;
    font-weight: 400;
}

.v-card-item {
    padding: 1.5rem 1.5em 0.5em 1.5em;
}

.v-card-item .v-card-title h3 {
    margin: 0px 0px 5px 0px;
    font-family: "Plus Jakarta Sans";
}

.v-card-text span {
    font-size: 16px;
    color: #A0AEC0;
    font-family: "Plus Jakarta Sans";
}

.mark-btn {
    margin: 120px 0px 0px 0px;
}

.mark-btn a {
    color: #fff;
    font-family: "Plus Jakarta Sans";
    font-size: 14px;
    display: flex;
    align-items: end;
    gap: 3px;
}


</style>
