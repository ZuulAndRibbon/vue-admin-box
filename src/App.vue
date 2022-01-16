<template>
  <el-config-provider :locale="locale">
    <router-view></router-view>
  </el-config-provider>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import {useRoute} from "vue-router";
import {useStore} from "vuex";
import {changeTitle} from "@/utils/system/title";
export default defineComponent({
  name: 'App',
  setup() {
    // set lang as en
    const route = useRoute()
    const store = useStore()
    store.commit('app/stateChange', { name: 'lang', value: 'en' })
    // changeTitle(route.meta.title)
    document.querySelector('html')!.setAttribute('lang', 'en')

    const i18n = useI18n()
    const locale = computed(() => {
      return {
        name: i18n.locale.value,
        el: i18n.messages.value[i18n.locale.value].el
      }
    })
    return {
      locale
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100vh;
}
</style>
