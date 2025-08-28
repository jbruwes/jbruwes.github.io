<template>
  <!-- Заголовок блока исходные данные хранятся в page.title -->
  <h1 class="text-3xl font-bold mb-4">{{ page.title }}</h1>
  <!-- Описание блока исходные данные находятся в page.description -->
  <p class="text-gray-700 mb-6">{{ page.description }}</p>

  <el-descriptions class="mt-12 not-prose" title="Кто я такой" :column="column + 1" border>
    <el-descriptions-item :rowspan="Number(!!column) + 1">
      <template #label>
        <div class="cell-item">
          <icon icon="line-md:image" class="inline-block align-text-bottom size-4 mr-1"></icon>Фото
        </div>
      </template>
      <icon icon="fa-solid:user-astronaut" class="size-24 mx-auto"></icon>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <icon icon="line-md:account" class="inline-block align-text-bottom size-4 mr-1"></icon>Имя
        </div>
      </template>
      <el-tag>Сергей Брюсов</el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <icon icon="line-md:telegram" class="inline-block align-text-bottom size-4 mr-1"></icon>Телеграм
        </div>
      </template>
      <el-tag><el-link href="https://t.me/jbruwes" target="_blank" class="hover:no-underline" size="small">@jbruwes</el-link></el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <icon icon="line-md:map-marker-alt" class="inline-block align-text-bottom size-4 mr-1"></icon>Место на глобусе
        </div>
      </template>
      <el-tag>Калининград</el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
         <icon icon="tabler:brand-vk" class="inline-block align-text-bottom size-4 mr-1"></icon>
          ВКонтакте
        </div>
      </template>
      <el-tag><el-link href="https://vk.com/jbruwes" target="_blank" class="hover:no-underline" size="small">@jbruwes</el-link></el-tag>
    </el-descriptions-item>
  </el-descriptions>


</template>

<script setup lang="js">
// импорт инджектора из vue
import { inject, computed } from 'vue';

import { breakpointsTailwind, useBreakpoints } from '@vueuse/core';

const breakpoints = useBreakpoints(breakpointsTailwind);
const smaller = [breakpoints.smaller('md'), breakpoints.smallerOrEqual('lg')];
const column = computed(() => smaller.filter(({value})=> !value).length);

// деструктуируем id из props
const { id } = defineProps({
  id: {
    type: String,
    required: true
  }
});

// ижектируем ассоциативный массив pages
const pages = inject('pages');

// получаем текущую страницу из ассоциативного массива pages по id
const page = pages[id];
</script>