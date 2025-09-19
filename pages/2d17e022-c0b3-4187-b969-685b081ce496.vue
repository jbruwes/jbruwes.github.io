<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/vuebro/vuebro.ru" target="_blank" rel="noopener noreferrer"
                class="underline">https://github.com/vuebro/vuebro.ru</a></dd>
        <dt class="font-bold text-right">Русская версия сайта:</dt>
        <dd><a href="https://vuebro.ru" target="_blank" class="underline"
                rel="noopener noreferrer">https://vuebro.ru</a></dd>
        <dt class="font-bold text-right">Английская версия сайта:</dt>
        <dd><a href="https://vuebro.github.io" target="_blank" class="underline"
                rel="noopener noreferrer">https://vuebro.github.io</a></dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue, ElementPlus, TailwindCSS, Vue Router, VueBro, HighlightJS, Vue I18n, Iconify</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Создание сайта проекта VueBro</dd>
    </dl>
    <p>Самое трудное испытание для программиста - это не написание кода, а необходимость его документировать и объяснять
        другим как он работает. Именно для решения этой тяжелой задачи и был создан сайт <a href="https://vuebro.ru"
            target="_blank" class="underline" rel="noopener noreferrer">https://vuebro.ru</a>.</p>
    <p>А если серьезно, то сайт призван помочь разработчикам, которые используют VueBro, разобраться в его работе и
        научиться его использовать. Для этого на сайте представлены примеры использования VueBro, а также описание его
        возможностей.</p>
    <p>Сайт содержит следующие разделы:</p>
    <ul>
        <li>Ссылки на последнии версии для загрузки;</li>
        <li>Галерея со скриншотами;</li>
        <li>Раздел с документацией, в которой подробно описаны основы работы с VueBro;</li>
        <li>Раздел с примерами подключения различных фреймворков к VueBro;</li>
        <li>Целый блок, в котором тезисно расписаны преймущества использования и описание основных возможностей VueBro;
        </li>
        <li>Раздел, содержащий инструкции от облачных провайдеров по развертываню статического хостинга в хранилище S3
            для подключения VueBro.</li>
    </ul>
    <p>Сайт полностью статический и развернут на GitHub Pages. Для его создания использовался VueBro. Также имеется версия
        сайта на английском языке, которая развернута на GitHub Pages в отдельном репозитории.</p>
    <p>Сайт является открытым и доступен для просмотра и скачивания по адресу <a href="https://github.com/vuebro/vuebro.ru"
            target="_blank" class="underline" rel="noopener noreferrer">https://github.com/vuebro/vuebro.ru</a>.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { pid } = defineProps(["pid"]),
    the = inject("pages")[pid];

</script>
