<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Зеркало сайта на github:</dt>
        <dd><a href="https://jbruwes.github.io/nosacheva.ru" target="_blank" class="underline">https://jbruwes.github.io/nosacheva.ru</a>
        </dd>
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/jbruwes/nosacheva.ru"
                target="_blank" class="underline">https://github.com/jbruwes/nosacheva.ru</a>
        </dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue, Fomantic UI, Element Plus</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Перенести сайт на платформу VueBro</dd>
    </dl>
    <p>Сайт <a href="https://nosacheva.ru" target="_blank">nosacheva.ru</a> в каком-то роде архивный, светлая память
        Наталие Григорьевне. Поэтому было решено перенести его на платформу <a target="_blank"
            href="https://vuebro.ru">VueBro</a> с минимальными изменениями. Это был интересный эксперимент,
        доказывающий, что современные технологии в лице Vue.js могут лекго уживаться с такими динозаврами веб
        разработки, как jQuery, Fomantic UI и Jarallax.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { id } = defineProps(["id"]),
    the = inject("pages")[id];
</script>
