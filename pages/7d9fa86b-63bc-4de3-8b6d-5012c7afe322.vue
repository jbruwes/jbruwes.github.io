<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/vuebro/vuebro" target="_blank" rel="noopener noreferrer"
                class="underline">https://github.com/vuebro/vuebro</a></dd>
        <dt class="font-bold text-right">Сайт проекта:</dt>
        <dd><a href="https://vuebro.ru" target="_blank" class="underline"
                rel="noopener noreferrer">https://vuebro.ru</a></dd>
        <dt class="font-bold text-right">Веб приложение:</dt>
        <dd><a href="https://run.vuebro.ru" target="_blank" class="underline"
                rel="noopener noreferrer">https://run.vuebro.ru</a></dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Создание комплексного инструмента для быстрого изготовления сайтов на Vue без необходимости развертывания
            среды разработки</dd>
    </dl>
    <p>Сначала была идея, очень простая идея о том, что любой сайт можно представить в виде древовидной структуры,
        листья которой суть страницы сайта. Соответственно, структуру можно записать в файл json, туда же атрибуты
        каждой страницы а также названия html файлов и вот, готова навигация по сайту. Само собой напрашивается создать
        программу наподобие блокнота с деревом файлов, чтобы автоматизировать создание сайта.</p>
    <p>Идея появилась в начале нулевых, в те давние времена, когда еще не
        было формата json и даже jQuery еще не было. Тем не менее, скоро появился первый прототип, написанный на дельфи.
        Он позволял создавать простые сайты на локальном диске и синхронизировать их с веб сервером по протоколу ftp. С
        тех времен много воды утекло, однако идея не умирала, программа развивалась вместе с интернет технологиями.
        Программа была несколько раз переписана, были разные эксперименты, обкатывались новые идеи. Переворот случился в
        момент выхода фреймворка Vue. Файлы html удалось заменить файлами
        HTML-подобного формата, называемого однофайловыми
        компонентами (также
        известного как *.vue файлы,
        сокращённо называемых SFC), с задачей навигации прекрасно стал справляться официальный Vue Router, а синтаксис
        шаблонов, используемый Vue дал возможность рендерить на страницах информацию из файла "index.json". В нём как и
        в более ранних версиях хранится то самое дерево сайта, со всей структурой и атрибутами.</p>
    <p>Важной задачей было сохранение того духа веб разработки, когда для создания сайта нужен был лишь notepad.exe,
        прямые руки и браузер. Поэтому сейчас можно <a href="https://github.com/vuebro/vuebro/releases/latest"
            rel="noopener noreferrer" target="_blank">скачать и установить VueBro для Linux, Windows и macOS</a> или
        просто открыть <a href="https://run.vuebro.ru" target="_blank"
            rel="noopener noreferrer">https://run.vuebro.ru</a> и начать разработку. С чего начать, хорошо описано в
        документации: <a href="https://vuebro.ru/документация/старт/" rel="noopener noreferrer"
            target="_blank">https://vuebro.ru/документация/старт/</a>.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { id } = defineProps(["id"]),
    the = inject("pages")[id];

</script>
