<template>
  <!-- Заголовок блока исходные данные хранятся в page.title -->
  <h1 class="text-3xl font-bold mb-4">{{ page.title }}</h1>
  <!-- Описание блока исходные данные находятся в page.description -->
  <p class="text-gray-700 mb-6">{{ page.description }}</p>

  <el-descriptions class="mt-12 not-prose" title="Кто я такой" :column="3" border>
    <el-descriptions-item :rowspan="2" :width="140" align="center">
      <template #label>
        <div class="cell-item">
          <div class="i-line-md:image inline-block align-text-bottom size-4 mr-1"></div>Фото
        </div>
      </template>
      <div class="i-fa-solid:user-astronaut size-24 mx-auto"></div>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <div class="i-line-md:account inline-block align-text-bottom size-4 mr-1"></div>Имя
        </div>
      </template>
      <el-tag>Сергей Брюсов</el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <div class="i-line-md:telegram inline-block align-text-bottom size-4 mr-1"></div>Телеграм
        </div>
      </template>
      <el-tag><el-link href="https://t.me/jbruwes" target="_blank" class="hover:no-underline" size="small">@jbruwes</el-link></el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
          <div class="i-line-md:map-marker-alt inline-block align-text-bottom size-4 mr-1"></div>Место на глобусе
        </div>
      </template>
      <el-tag>Калининград</el-tag>
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="cell-item">
         <div class="i-tabler:brand-vk inline-block align-text-bottom size-4 mr-1"></div>
          ВКонтакте
        </div>
      </template>
      <el-tag><el-link href="https://vk.com/jbruwes" target="_blank" class="hover:no-underline" size="small">@jbruwes</el-link></el-tag>
    </el-descriptions-item>
  </el-descriptions>


</template>

<script setup lang="js">
// импорт инджектора из vue
import { inject } from 'vue'

import {
  Iphone,
  Location,
  OfficeBuilding,
  Tickets,
  User,
} from '@element-plus/icons-vue'

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