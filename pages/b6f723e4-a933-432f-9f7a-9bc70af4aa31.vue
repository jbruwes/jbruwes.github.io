<template>
    <div class="container mx-auto">
        <!-- Заголовок блока исходные данные хранятся в page.title -->
        <h1 class="text-3xl font-bold mb-4">{{ page.title }}</h1>
        <!-- Описание блока исходные данные находятся в page.description -->
        <p class="text-gray-700 mb-6">{{ page.description }}</p>
    </div>
</template>

<script setup lang="js">
// импорт инджектора из vue
import { inject } from 'vue'

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