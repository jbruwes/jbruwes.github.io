<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Зеркало сайта на github:</dt>
        <dd><a href="https://jbruwes.github.io/savamed.ru" target="_blank" class="underline">https://jbruwes.github.io/savamed.ru</a>
        </dd>
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/jbruwes/savamed.ru" target="_blank" class="underline">https://github.com/jbruwes/savamed.ru</a>
        </dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue, Tailwind CSS, Element Plus, Vue I18n</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Добавить английскую версию сайта</dd>
    </dl>
    <p>Предыдущая версия сайта savamed.ru была выполнена с помощью фреймворка <a href="https://fomantic-ui.com"
            target="_blank">Fomantic UI</a>. Новая версия сайта собрана с помощью редактора <a target="_blank"
            href="https://vuebro.ru">VueBro</a>. Для оформления был использован фреймворк <a
            href="https://element-plus.org" target="_blank">Element Plus</a>. Перевод был выполнен на базе пакета <a
            href="https://vue-i18n.intlify.dev" target="_blank">Vue I18n</a>. Для анимаций была использована библиотека
        CSS эффектов <a href="https://animate.style" target="_blank">Animate.css</a> и <a href="ianlunn.github.io/Hover"
            target="_blank">Hover.css</a>. Сайт использует Vue.js и классы Tailwind CSS. SFC файлы подгружаются
        динамически благодаря <router-link to="/loader-sfc/">@vuebro/loader-sfc</router-link>, а значит  сайт работает без
        предварительной компиляции на любом статическом хостинге.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { pid } = defineProps(["pid"]),
    the = inject("pages")[pid];
</script>
