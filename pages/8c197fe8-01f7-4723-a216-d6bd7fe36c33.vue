<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Зеркало сайта на github:</dt>
        <dd><a href="https://jbruwes.github.io/card" target="_blank" class="underline">https://jbruwes.github.io/card</a>
        </dd>
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/jbruwes/card" target="_blank" class="underline">https://github.com/jbruwes/card</a>
        </dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue, TresJS, Element Plus</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Сделать визуально впечатляющее приложение с помощью веб-технологий</dd>
    </dl>
    <p>Логика приложения проста и понятна - имеем колоду метафорических ассоциативных карт, из которых раз в сутки
        пользователь может вытянуть одну и только одну карту. После этого судьбоносного шага и строго до конца суток
        пользователь удаляется заниматься самоанализом. Такие приложения не редкость в интернете, но все которые мне
        попадались, были написаны технарями. Они все как одно невыразительны, в них нет азарта, драмы. Они механистичны
        и предлагаю пользователю следующее - вот человек, представь, этот прямоугольник похож на карту. Ну кликни на
        него, ну вот тебе картинка. До новых встреч!</p>
    <p>Я же решил сделать программку таким образом, чтобы она как минимум запоминалась. Технически мини-приложение
        основано на широко известной демке "Three Js Ghost Card Animation", но переписано полностью на TresJS, творчески
        переработано, кое-где подправлено и улучшено. Пример с картой вообще интересен тем, что использует постэффект,
        который рендерится на текстуру. Именно так рождается фиолетовое пламя, которым объят череп.</p>
    <p>Всё приложение состоит из двух экранов. Один — дьявольски
        ужасный, с картой-черепом, символизирующей фатум, второй — пасторальный и намеренно умиротворённый. На нём
        показывается выбранная карта.</p>
    <p>
        Ещё из интересного: для gl-анимаций используется GSAP, остальные анимации сделаны посредством CSS.</p>
    <p>
        Приложение работает как просто в браузере: <a href="https://jbruwes.github.io/card" target="_blank" rel="noopener noreferrer">https://jbruwes.github.io/card</a>, храня при этом выбранную карту дня в
        локальном хранилище, так и в Telegram по ссылке <a href="https://t.me/abb_psy_bot?startapp" target="_blank" rel="noopener noreferrer">https://t.me/abb_psy_bot?startapp</a>, либо во «ВКонтакте» — <a href="https://vk.com/app53994795" target="_blank" rel="noopener noreferrer">https://vk.com/app53994795</a>.
        В случае запуска в социальных сетях выбранная карта хранится в
        соответствующих облачных хранилищах.</p>
    <p><br></p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { id } = defineProps(["id"]),
    the = inject("pages")[id];
</script>
