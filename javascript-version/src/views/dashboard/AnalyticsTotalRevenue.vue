<script setup>
import VueApexCharts from 'vue3-apexcharts'
import {
  useDisplay,
  useTheme,
} from 'vuetify'
import { hexToRgb } from '@layouts/utils'
import { ref, reactive } from 'vue'


const vuetifyTheme = useTheme()
const display = useDisplay()

const array = ref([1,2,3,4,5])

</script>

<template>
  <VCard class="sessions-list-sec">
    <VRow no-gutters>
      <VCol
        cols="12"
        sm="12"
        xl="12"
      >
        <!-- <VCardItem class="pb-0">
          <VCardTitle>Total Revenue</VCardTitle>

          <template #append>
            <div class="me-n3">
              <MoreBtn />
            </div>
          </template>
        </VCardItem>

        <VueApexCharts
          id="bar-chart"
          type="bar"
          :height="336"
          :options="chartOptions.bar"
          :series="series"
        /> -->

      <div class="my_sessions_card">
        <h3>My Sessions</h3>
        <div class="session-scroll">
        <div class="view-session-card" v-for="item in array">
          <div class="session-flex">
          <div class="session-image">
            <img src="../../assets/images/cards/session-image.png" alt="">
          </div>
          <div class="session-name">
            <h4>UI/UX Design</h4>
            <p>Session ID: 199 - 177 - 0323</p>
            <p>Schedule Time:  Tue 20 May 2024 19:00</p>
            <p>Owner: FRB1235476</p>
          </div>
        </div>
          <div class="view-sesssion-button">
             <div class="short-edit-delete">
              <div class="short-list">
                <h6><i class='bx bxs-star'></i> Short List</h6>
              </div>
              <div class="delete-button">
                <h5><i class='bx bx-trash'></i> Delete</h5>
              </div>
              <div class="edit-button">
                <h5><i class='bx bxs-pencil'></i> Edit</h5>
              </div>
             </div>
             <a href="#">View Session</a>
          </div>
        </div>
      </div>
      </div>

      </VCol>

      <!-- <VCol
        cols="12"
        sm="4"
        xl="4"
      >
        <VCardText class="text-center">
          <VBtn
            size="small"
            variant="tonal"
            append-icon="bx-chevron-down"
            class="mt-4"
          >
            2023
            <VMenu activator="parent">
              <VList>
                <VListItem
                  v-for="(item, index) in ['2023', '2022', '2021']"
                  :key="index"
                  :value="item"
                >
                  <VListItemTitle>{{ item }}</VListItemTitle>
                </VListItem>
              </VList>
            </VMenu>
          </VBtn>

          <VueApexCharts
            type="radialBar"
            :height="200"
            :options="chartOptions.radial"
            :series="[78]"
            class="mt-6"
          />

          <p class="font-weight-medium text-high-emphasis mb-7">
            62% Company Growth
          </p>
          <div class="d-flex align-center justify-center gap-x-8 gap-y-4 flex-wrap">
            <div
              v-for="data in balanceData"
              :key="data.year"
              class="d-flex align-center gap-3"
            >
              <VAvatar
                :icon="data.icon"
                :color="data.color"
                size="38"
                rounded
                variant="tonal"
              />

              <div class="text-start">
                <span class="text-sm"> {{ data.year }}</span>
                <h6 class="text-base font-weight-medium">
                  {{ data.amount }}
                </h6>
              </div>
            </div>
          </div>
        </VCardText>
      </VCol> -->
    </VRow>
  </VCard>
</template>

<style lang="css">

.sessions-list-sec {
    border-radius: 20px;
    background: linear-gradient(127deg, rgba(6, 11, 40, 0.94) 19.41%, rgba(10, 14, 35, 0.49) 76.65%);
    backdrop-filter: blur(60px);
}

.my_sessions_card {
    padding: 30px;
}

.session-scroll {
    height: 400px;
    overflow-y: scroll;
    padding: 0px 10px 0px 0px;
}

.session-scroll::-webkit-scrollbar {
  width: 10px;
  border-radius: 50px;
}

/* Track */
.session-scroll::-webkit-scrollbar-track {
  background: #060b28f0; 
  border-radius: 50px;
}
 
/* Handle */
.session-scroll::-webkit-scrollbar-thumb {
  background: #262c4e; 
  border-radius: 50px;
}

.my_sessions_card h3 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 20px;
    font-weight: 700;
    background: linear-gradient(127deg, rgb(6 11 41) 19.41%, rgb(10 22 60) 76.65%);
    margin: 0px 0px 20px 0px;
}

.view-session-card {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-radius: 20px;
    background: linear-gradient(127deg, rgba(24, 29, 60, 0.94) 19.41%, rgba(10, 14, 35, 0.49) 76.65%);
    backdrop-filter: blur(60px);
    margin: 15px 0px 0px 0px;
}



.session-name h4 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 18px;
    text-transform: uppercase;
    font-weight: 500;
    margin: 0px 0px 3px 0px;
}

.session-name p {
    margin: 0px;
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    font-weight: 400;
}

.session-image {padding: 10px;}

.session-image {
    padding: 15px 10px;
}

.short-edit-delete {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 6px;
    margin: 0px 0px 25px 0px;
}

.short-list h6 {
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    font-weight: 400;
    color: #A0AEC0;
    cursor: pointer;
}

.delete-button h5 {
    font-weight: 400;
    color: #F53C2B;
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    text-transform: uppercase;
    cursor: pointer;
}


.view-sesssion-button a {
    margin: 10px 0px 10px 0px;
    padding: 12px 25px;
    border-radius: 12px;
    background: #0075FF;
    color: #fff;
    text-align: center;
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    border: 1px solid #0075FF;
    transition: all .6s ease;
}

.view-sesssion-button a:hover {
    background: transparent;
    color: #0075FF;
}

.view-sesssion-button {
    text-align: end;
    margin: 0px 20px 0px 0px;
}

.session-flex {
  display: flex;
  align-items: center
}

.edit-button h5 {
    text-transform: uppercase;
    font-weight: 400;
    font-size: 16px;
    cursor: pointer;
}


</style>
