<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/vuebro/loader-sfc-example" target="_blank" class="underline">@vuebro/loader-sfc-example</a></dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue, Vite, @vuebro/loader-sfc</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Продемонстрировать использование @vuebro/loader-sfc в приложении, собранным Vite</dd>
    </dl>
    <p>Идея проекта крайне проста:</p>
    <ol>
        <li>Создать типовое приложение Vite</li>
        <li>Провести минимальные манипуляции, необходимые для динамической загрузки посредством @vuebro/loader-sfc</li>
    </ol>
    <p>Типовое приложение создается с помощью команды:</p>
    <highlightjs language="bash" code="npm create vite@latest loader-sfc-example -- --template vue-ts" class="pa-0 -mx-4"></highlightjs>
    <p>После создания произведены следующие действия для загрузки HelloWorld.vue без предварительной компиляции:</p>
    <ol>
        <li>Файл vue.esm-browser.prod.js скоприрован с помощью плагина <a href="https://github.com/sapphi-red/vite-plugin-static-copy" target="_blank">vite-plugin-static-copy</a>
            в директорию assets при сборке проекта;</li>
        <li>Экстернализирован фреймворк Vue с помощью настроек Rollup для режима prod и плагина <a href="https://github.com/MilanKovacic/vite-plugin-externalize-dependencies" target="_blank">vite-plugin-externalize-dependencies</a> для dev режима;</li>
        <li>Добавлен "vue": "./assets/vue.esm-browser.prod.js" в importmap, чтобы Vue был доступен из модулей в
            браузере;</li>
        <li>Компонент HelloWorld.vue скопирован из директории /src/components в директорию /public/components, для того
            чтобы попадать в собранный проект в исходном виде.</li>
    </ol>
    <p>После этих небольших изменений в проект можно наконец-то изменить способ подключения SFC модуля:</p>
    <highlightjs language="html" :code="code" class="pa-0 -mx-4"></highlightjs>
    <p>Подробную инструкцию см. в описании репозитория <a href="https://github.com/vuebro/loader-sfc-example" target="_blank">@vuebro/loader-sfc-example</a>.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { id } = defineProps(["id"]),
    the = inject("pages")[id],
    code = `<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'

import { defineAsyncComponent } from 'vue'
import loadModule from '@vuebro/loader-sfc'

const HelloWorld = defineAsyncComponent(() => loadModule('./components/HelloWorld.vue'))
<\/script>

<template>
  ...
</template>

<style scoped>
...
<\/style>`;

</script>
