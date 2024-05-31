<script setup>
import AnalyticsCongratulations from '@/views/dashboard/AnalyticsCongratulations.vue'
import AnalyticsFinanceTabs from '@/views/dashboard/AnalyticsFinanceTab.vue'
import AnalyticsOrderStatistics from '@/views/dashboard/AnalyticsOrderStatistics.vue'
import AnalyticsProfitReport from '@/views/dashboard/AnalyticsProfitReport.vue'
import AnalyticsTotalRevenue from '@/views/dashboard/AnalyticsTotalRevenue.vue'
import AnalyticsTransactions from '@/views/dashboard/AnalyticsTransactions.vue'

// 👉 Images
import chart from '@images/cards/chart-success.png'
import card from '@images/cards/credit-card-primary.png'
import paypal from '@images/cards/paypal-error.png'
import wallet from '@images/cards/wallet-info.png'

import VueApexCharts from 'vue3-apexcharts'
import {
  useDisplay,
  useTheme,
} from 'vuetify'

const vuetifyTheme = useTheme()
const display = useDisplay()
import { hexToRgb } from '@layouts/utils'


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
  <VRow>
    <!-- 👉 Congratulations -->
    <VCol
      cols="12"
      md="5"
    >
      <AnalyticsCongratulations />
    </VCol>

    <VCol
      cols="12"
      sm="7"
    >
      <VRow>
        <!-- 👉 Profit -->
        <VCol
          cols="12"
          md="5"
        >
          <!-- <CardStatisticsVertical
            v-bind="{
              title: 'Profit',
              image: chart,
              stats: '$12,628',
              change: 72.80,
            }"
          /> -->
          <VCardText class="growth-card text-center">
          <!-- <VBtn
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
          </VBtn> -->

          <!-- radial chart -->
          <VueApexCharts
            type="radialBar"
            :height="200"
            :options="chartOptions.radial"
            :series="[78]"
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
        </VCol>

        <!-- 👉 Sales -->
        <VCol
          cols="12"
          md="7"
        >
          <!-- <CardStatisticsVertical
            v-bind="{
              title: 'Sales',
              image: wallet,
              stats: '$4,679',
              change: 28.42,
            }"
          /> -->
          <div class="performing-sessions-card">
            <div class="perform-head">
              <h4>Top Performing Sessions</h4>
              <div class="perform-menu">
                <span><i class='bx bx-dots-horizontal-rounded'></i></span>
              </div>
            </div>
            <div class="session-card">
              <div class="session-text">
                <h6>SessionID: 19022399</h6>
                <h6>People Interacted</h6>
              </div>
              <div class="people-percent">
                <h4>145 people</h4>
                <h4>90%</h4>
              </div>
            </div>
            <div class="session-card">
              <div class="session-text">
                <h6>Session ID: 908SD232</h6>
                <h6>People Interacted</h6>
              </div>
              <div class="people-percent">
                <h4>200 people</h4>
                <h4>78%</h4>
              </div>
            </div>
          </div>
        </VCol>
      </VRow>
    </VCol>

    <!-- 👉 Total Revenue -->
    <VCol
      cols="12"
      md="7"
      order="2"
      order-md="1"
    >
      <AnalyticsTotalRevenue />
      
    </VCol>

    <VCol
      cols="12"
      sm="8"
      md="5"
      order="1"
      order-md="2"
    >
      <VRow>
        <!-- 👉 Payments -->
        <VCol
          cols="12"
          sm="6"
        >
          <CardStatisticsVertical
            v-bind=" {
              title: 'Payments',
              image: paypal,
              stats: '$2,468',
              change: -14.82,
            }"
          />
        </VCol>

        <!-- 👉 Revenue -->
        <VCol
          cols="12"
          sm="6"
        >
          <CardStatisticsVertical
            v-bind="{
              title: 'Transactions',
              image: card,
              stats: '$14,857',
              change: 28.14,
            }"
          />
        </VCol>
      </VRow>

      <VRow>
        <!-- 👉 Profit Report -->
        <VCol
          cols="12"
          sm="12"
        >
          <AnalyticsProfitReport />
        </VCol>
      </VRow>
    </VCol>

    <!-- 👉 Order Statistics -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsOrderStatistics />
    </VCol>

    <!-- 👉 Tabs chart -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsFinanceTabs />
    </VCol>

    <!-- 👉 Transactions -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsTransactions />
    </VCol>
  </VRow>
</template>




<style scoped> 

.welcomeback-card {
  background: url(../assets/images/cards/mark-johshan-bg.png) no-repeat top center;
  background-size: cover;
  height: 100%;
  width: 100%
}

.v-card-item {
    padding: 1.1rem 1.5rem;
}

.v-card-item__content h5 {
    font-size: 16px;
    font-family: 'Plus Jakarta Sans';
    color: #A0AEC0;
    font-weight: 400;
}

.growth-card {
  background: linear-gradient(127deg, rgba(6, 11, 40, 0.94) 19.41%, rgb(45 63 153 / 13%) 76.65%);
  backdrop-filter: blur(60px);
  border-radius: 20px;
}

.performing-sessions-card {
    padding: 20px;
    border-radius: 20px;
    background: linear-gradient(127deg, rgba(6, 11, 40, 0.74) 28.26%, rgba(14, 21, 58, 0.71) 91.2%);
    backdrop-filter: blur(60px);
}

.perform-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0px 0px 20px 0px;
}

.perform-menu span {
    color: #7551FF;
    font-size: 25px;
    background: #ffffff14;
    padding: 6px 4px 0px 4px;
    border-radius: 10px;
    cursor: pointer;
}

.perform-head h4 {
    font-family: "Plus Jakarta Sans";
    font-size: 18px;
}

.session-card {
    padding: 19px;
    margin: 14px 10px;
    border-radius: 20px;
    background: linear-gradient(127deg, #060C29 28.26%, rgba(4, 12, 48, 0.50) 91.2%);
    backdrop-filter: blur(60px);
}

.session-text {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.session-text h6 {
    font-family: "Plus Jakarta Sans";
    font-size: 14px;
    font-weight: 400;
    color: #A0AEC0;
}

.people-percent h4 {
    font-family: "Plus Jakarta Sans";
    font-size: 18px;
    color: #ffff;
    margin: 5px 0px;
}

.people-percent {
    display: flex;
    align-items: center;
    justify-content: space-between;
}






</style>
