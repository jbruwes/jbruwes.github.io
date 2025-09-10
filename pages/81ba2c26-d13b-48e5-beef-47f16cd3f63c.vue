<template>
    <h1>{{ the.title }}</h1>
    <p>{{ the.description }}</p>
    <el-divider></el-divider>
    <dl class="grid grid-cols-2 gap-x-4 w-fit not-prose">
        <dt class="font-bold text-right">Адрес репозитория:</dt>
        <dd><a href="https://github.com/vuebro/loader-sfc" target="_blank" class="underline">https://github.com/vuebro/loader-sfc</a></dd>
        <dt class="font-bold text-right">Стек технологий:</dt>
        <dd>Vue</dd>
        <dt class="font-bold text-right">Решаемая задача:</dt>
        <dd>Загружать, компилировать и импортировать однофайловые компоненты Vue (они же файлы *.vue, сокращённо
            SFC, от Single File Component)</dd>
    </dl>
    <p>Vue в отличии от многих аналогичных фреймворков, можно подключать напрямую из CDN в обычную HTML страницу.
    </p>
    <p>Как сказано в документации по Vue.js в разделе <a
            href="https://ru.vuejs.org/guide/quick-start.html#using-vue-from-cdn" target="_blank">Использование Vue
            с помощью CDN</a>:</p>
    <blockquote cite="https://ru.vuejs.org/guide/quick-start.html#using-vue-from-cdn">
        При использовании Vue из CDN нет никакого «шага сборки». Это значительно упрощает конфигурацию и подходит
        для улучшения статического HTML или для интеграции с бэкенд-фреймворком. Но в таком случае не получится
        использовать синтаксис однофайловых компонентов (SFC).
    </blockquote>
    <p>При этом SFC имеют множество преимуществ, о которых также рассказано в документации по Vue.js в разделе <a
            href="https://ru.vuejs.org/guide/scaling-up/sfc.html#why-sfc" target="_blank">Почему SFC</a>.</p>
    <p>Задачу использования SFC без этапа сборки непосредственно в браузере решает пакет @vuebro/loader-sfc. Он
        позволяет загружать SFC модули в качестве <a
            href="https://ru.vuejs.org/guide/components/async.html">асинхронного компонента</a>. Это удобно
        использовать как в простых статических сайтах, так и в сложных Vue приложениях, где возникает потребность
        загружать некоторые SFC компоненты в процессе эксплуатации исключая повторную сборку и компиляцию всего
        приложения.</p>
    <h3>Как это работает</h3>
    <p>Однофайловые компоненты Vue - формат, специфический для фреймворка, который нужно предварительно
        скомпилировать в обычный JavaScript и CSS с помощью @vue/compiler-sfc. Скомпилированный однофайловый
        компонент это обычный ES-модуль JavaScript. А значит, последовательность действий такая:</p>
    <ol>
        <li>С помощью <a href="https://developer.mozilla.org/ru/docs/Web/API/Fetch_API" target="_blank">Fetch
                API</a> загружается исходный файл .vue;</li>
        <li>Следом используется библиотека <a href="sucrase.io" target="_blank">Sucrase</a> для преобразования
            typescript и jsx;</li>
        <li>Полученные исходники компилируются в обычный ES-модуль JavaScript с помощью <a
                href="https://github.com/vuejs/core/tree/main/packages/compiler-sfc"
                target="_blank">@vue/compiler-sfc</a>;</li>
        <li>Далее ES-модуль преобразуется в Base64 и динамически импотируется из Data URL.</li>
    </ol>
    <p>Таким образом можно импортировать .vue файлы без этапа сборки даже из других SFC модулей:</p>
    <highlightjs language="html" :code="code" class="pa-0 -mx-4"></highlightjs>
    <p>Надо отметить, что широко известен, по крайней мере один аналог @vuebro/loader-sfc. Это vue3-sfc-loader -
        прекрасная библиотека, которая отлично выполняет свою работу. Однако она давно не обновляется, использует
        несколько устаревшие webpack и babel и тянет за собой поддержку Vue2 а также СommonJS модулей.</p>
</template>

<script setup lang="js">
import { inject } from 'vue';

const { pid } = defineProps(["pid"]),
    the = inject("pages")[pid],
    code = `<script setup>
import { defineAsyncComponent } from "vue";
import loadModule from "@vuebro/loader-sfc";

const AdminPage = defineAsyncComponent(() =>
  loadModule('./components/AdminPageComponent.vue')
);
<\/script>

<template>
  <AdminPage />
</template>`;

</script>
