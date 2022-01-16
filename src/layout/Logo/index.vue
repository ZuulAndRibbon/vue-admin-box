<template>
  <router-link
      key="expand"
      class="sidebar-logo-link"
      to="/"
  >
    <div class="logo-container">
      <img src="@/assets/logo.png" alt="" class="sidebar-logo" :class="isCollapse?'sidebar-logo-collapse':''">
      <h1 v-if="!isCollapse">{{ $t(systemTitle) }}</h1>
    </div>
  </router-link>

</template>

<script lang="ts">
import {defineComponent, computed} from 'vue'
import {useStore} from 'vuex'
import {systemTitle} from '@/config'

export default defineComponent({
  setup() {
    const store = useStore()
    const isCollapse = computed(() => store.state.app.isCollapse)
    return {
      isCollapse,
      systemTitle
    }
  }
})
</script>

<style lang="scss" scoped>
.logo-container {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
  width: 100%;
  background-color: var(--system-logo-background);

  & .sidebar-logo {
    width: 26px;
    height: 26px;
    margin-right: 10px;
  }

  & .sidebar-logo-collapse{
    margin-right: 0px;
  }

  h1 {
    font-size: 18px;
    white-space: nowrap;
    color: var(--system-logo-color);
  }
}
</style>
