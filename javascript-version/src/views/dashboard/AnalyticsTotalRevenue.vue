<script setup>
import VueApexCharts from 'vue3-apexcharts'
import {
  useDisplay,
  useTheme,
} from 'vuetify'
import { hexToRgb } from '@layouts/utils'

const vuetifyTheme = useTheme()
const display = useDisplay()

const series = [
  {
    name: `${ new Date().getFullYear() - 1 }`,
    data: [
      18,
      7,
      15,
      29,
      18,
      12,
      9,
    ],
  },
  {
    name: `${ new Date().getFullYear() - 2 }`,
    data: [
      -13,
      -18,
      -9,
      -14,
      -5,
      -17,
      -15,
    ],
  },
]

const chartOptions = computed(() => {
  const currentTheme = vuetifyTheme.current.value.colors
  const variableTheme = vuetifyTheme.current.value.variables
  const disabledTextColor = `rgba(${ hexToRgb(String(currentTheme['on-surface'])) },${ variableTheme['disabled-opacity'] })`
  const primaryTextColor = `rgba(${ hexToRgb(String(currentTheme['on-surface'])) },${ variableTheme['high-emphasis-opacity'] })`
  const borderColor = `rgba(${ hexToRgb(String(variableTheme['border-color'])) },${ variableTheme['border-opacity'] })`
  
  return {
    bar: {
      chart: {
        stacked: true,
        parentHeightOffset: 0,
        toolbar: { show: false },
      },
      dataLabels: { enabled: false },
      stroke: {
        width: 6,
        lineCap: 'round',
        colors: [currentTheme.surface],
      },
      colors: [
        `rgba(${ hexToRgb(String(currentTheme.primary)) }, 1)`,
        `rgba(${ hexToRgb(String(currentTheme.info)) }, 1)`,
      ],
      legend: {
        offsetX: -10,
        position: 'top',
        fontSize: '14px',
        horizontalAlign: 'left',
        fontFamily: 'Public Sans',
        labels: { colors: currentTheme.secondary },
        itemMargin: {
          vertical: 4,
          horizontal: 10,
        },
        markers: {
          width: 8,
          height: 8,
          radius: 10,
          offsetX: -4,
        },
      },
      states: {
        hover: { filter: { type: 'none' } },
        active: { filter: { type: 'none' } },
      },
      grid: {
        borderColor,
        padding: { bottom: 5 },
      },
      plotOptions: {
        bar: {
          borderRadius: 10,
          columnWidth: '30%',
          endingShape: 'rounded',
          startingShape: 'rounded',
        },
      },
      xaxis: {
        axisTicks: { show: false },
        crosshairs: { opacity: 0 },
        axisBorder: { show: false },
        categories: [
          'Jan',
          'Feb',
          'Mar',
          'Apr',
          'May',
          'Jun',
          'Jul',
        ],
        labels: {
          style: {
            fontSize: '14px',
            colors: disabledTextColor,
            fontFamily: 'Public Sans',
          },
        },
      },
      yaxis: {
        labels: {
          style: {
            fontSize: '14px',
            colors: disabledTextColor,
            fontFamily: 'Public Sans',
          },
        },
      },
      responsive: [
        {
          breakpoint: display.thresholds.value.xl,
          options: { plotOptions: { bar: { columnWidth: '43%' } } },
        },
        {
          breakpoint: display.thresholds.value.lg,
          options: { plotOptions: { bar: { columnWidth: '50%' } } },
        },
        {
          breakpoint: display.thresholds.value.md,
          options: { plotOptions: { bar: { columnWidth: '42%' } } },
        },
        {
          breakpoint: display.thresholds.value.sm,
          options: { plotOptions: { bar: { columnWidth: '45%' } } },
        },
      ],
    },
    radial: {
      chart: { sparkline: { enabled: true } },
      labels: ['Growth'],
      stroke: { dashArray: 5 },
      colors: [`rgba(${ hexToRgb(String(currentTheme.primary)) }, 1)`],
      states: {
        hover: { filter: { type: 'none' } },
        active: { filter: { type: 'none' } },
      },
      fill: {
        type: 'gradient',
        gradient: {
          shade: 'dark',
          opacityTo: 0.6,
          opacityFrom: 1,
          shadeIntensity: 0.5,
          stops: [
            30,
            70,
            100,
          ],
          inverseColors: false,
          gradientToColors: [currentTheme.primary],
        },
      },
      plotOptions: {
        radialBar: {
          endAngle: 150,
          startAngle: -140,
          hollow: { size: '55%' },
          track: { background: 'transparent' },
          dataLabels: {
            name: {
              offsetY: 25,
              fontWeight: 600,
              fontSize: '16px',
              color: currentTheme.secondary,
              fontFamily: 'Public Sans',
            },
            value: {
              offsetY: -15,
              fontWeight: 500,
              fontSize: '24px',
              color: primaryTextColor,
              fontFamily: 'Public Sans',
            },
          },
        },
      },
      responsive: [
        {
          breakpoint: 900,
          options: { chart: { height: 200 } },
        },
        {
          breakpoint: 735,
          options: { chart: { height: 200 } },
        },
        {
          breakpoint: 660,
          options: { chart: { height: 200 } },
        },
        {
          breakpoint: 600,
          options: { chart: { height: 280 } },
        },
      ],
    },
  }
})

const balanceData = [
  {
    icon: 'bx-dollar',
    amount: '$32.5k',
    year: '2023',
    color: 'primary',
  },
  {
    icon: 'bx-wallet',
    amount: '$41.2k',
    year: '2022',
    color: 'info',
  },
]
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
        <div class="view-session-card">
          <div class="session-image">
            <img src="../../assets/images/cards/session-image.png" alt="">
          </div>
          <div class="session-name">
            <h4>UI/UX Design</h4>
            <p>Session ID: 199 - 177 - 0323</p>
            <p>Schedule Time:  Tue 20 May 2024 19:00</p>
            <p>Owner: FRB1235476</p>
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
    padding: 20px;
}

.my_sessions_card h3 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 20px;
    font-weight: 700;
}


.my_sessions_card {
      padding: 30px;
  }

.my_sessions_card h3 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 20px;
    font-weight: 700;
}

.view-session-card {
    display: flex;
    align-items: center;
    border-radius: 20px;
    background: linear-gradient(127deg, rgba(24, 29, 60, 0.94) 19.41%, rgba(10, 14, 35, 0.49) 76.65%);
    backdrop-filter: blur(60px);
    margin: 15px 0px 0px 0px;
    gap: 5px;
}


.session-name h4 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    text-transform: uppercase;
    font-weight: 500;
} 

.session-name h4 {
    color: #FFF;
    font-family: "Plus Jakarta Sans";
    font-size: 16px;
    text-transform: uppercase;
    font-weight: 500;
    margin: 0px 0px 3px 0px;
}

.session-name p {
    margin: 0px;
    font-family: "Plus Jakarta Sans";
    font-size: 12px;
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
}

.view-session-card {
    width: 100%;
}

.short-list h6 {
    font-family: "Plus Jakarta Sans";
    font-size: 12px;
    font-weight: 400;
    color: #A0AEC0;
}

.delete-button h5 {
    font-weight: 400;
    color: #F53C2B;
    font-family: "Plus Jakarta Sans";
    font-size: 12px;
    text-transform: uppercase;
}




</style>
