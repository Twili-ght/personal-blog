<script setup lang="ts">
import { ref } from 'vue'
import { inBrowser } from 'vitepress'

import type { NavLink } from '../.vitepress/theme/types'
import { NAV_DATA } from './data'

const M_RECENT_LINKS_KEY = 'Recent'
const EXPIRATION_TIME = 24 * 60 * 60 * 1000
const getItems = () => {
  if (!inBrowser) {
    return []
  }
  const value = localStorage.getItem(M_RECENT_LINKS_KEY)
  if (value) {
    try {
      return JSON.parse(value)
    } catch (e) {
      return []
    }
  }
  return []
}

const items = ref<NavLink[]>(getItems())

const handleClick = (data: NavLink) => {
  const chinaTime = new Date().toLocaleString("zh-CN", { timeZone: "Asia/Shanghai" });
  let newData = items.value.filter((item) => item.link !== data.link)
  newData.unshift(data)
  if (newData.length > 4) {
    newData = newData.slice(0, 4)
  }
  localStorage.setItem(M_RECENT_LINKS_KEY, JSON.stringify(newData))
  items.value = newData
}
/**
 * 设置 localStorage 存储时间
 */
const  RemoveStorage=()=>{

}
</script>

<template>
  <MNavLinks v-if="items.length" title="最近使用" @nav-click="handleClick" :items="items" />
  <MNavLinks v-for="item in NAV_DATA" v-bind="item" @nav-click="handleClick" />
</template>

<style src="./index.scss"></style>
