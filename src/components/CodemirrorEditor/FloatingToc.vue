<script setup lang='ts'>
import { List } from 'lucide-vue-next'

const store = useStore()

const isOpenHeadingSlider = ref(false)
</script>

<template>
  <div
    class="bg-background absolute left-0 top-0 border rounded-2 rounded-lt-none p-2 text-sm shadow"
    @mouseenter="() => (isOpenHeadingSlider = true)"
    @mouseleave="() => (isOpenHeadingSlider = false)"
  >
    <List class="size-6" />
    <ul
      class="overflow-auto transition-all"
      :class="{
        'max-h-0 w-0': !isOpenHeadingSlider,
        'max-h-100 w-60 mt-2': isOpenHeadingSlider,
      }"
    >
      <li
        v-for="(item, index) in store.titleList"
        :key="index"
        class="line-clamp-1 py-1 leading-6 hover:bg-gray-300 dark:hover:bg-gray-600"
        :style="{ paddingLeft: `${item.level - 0.5}em` }"
      >
        <a :href="item.url">
          {{ item.title }}
        </a>
      </li>
    </ul>
  </div>
</template>
