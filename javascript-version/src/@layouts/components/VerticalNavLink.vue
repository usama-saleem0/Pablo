<script setup>
const props = defineProps({
  item: {
    type: null,
    required: true,
  },
})
</script>

<template>
  <li
    class="nav-link"
    :class="{ disabled: item.disable }"
  >
    <Component
      :is="item.to ? 'RouterLink' : 'a'"
      :to="item.to"
      :href="item.href"
    >
    <div class="tantan">

    
      <!-- <VIcon
        :icon="item.icon"
        class="nav-item-icon"
      /> -->
  <div class="sidebar-svg" v-html="item.icon"></div>

      <!-- <image :src="item.icon"/> -->

    </div>
      <!-- 👉 Title -->
      <span class="nav-item-title">
        {{ item.title }}
      </span>
    </Component>
  </li>
</template>

<style lang="scss" scoped>
.layout-vertical-nav {
  .nav-link a {
    display: flex;
    align-items: center;
    cursor: pointer;
  }
}



</style>
