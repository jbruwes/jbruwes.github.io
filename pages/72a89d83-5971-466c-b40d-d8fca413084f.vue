<template>
    <div class="container mx-auto px-4">
        <RouterView></RouterView>
    </div>
    <el-backtop></el-backtop>
</template>

<script setup lang="js">
import { getCurrentInstance } from "vue";
import ElementPlus from "element-plus";
import hljs from "highlight.js/lib/core";
import javascript from "highlight.js/lib/languages/javascript";
import css from "highlight.js/lib/languages/css";
import xml from "highlight.js/lib/languages/xml";
import hljsVuePlugin from "@highlightjs/vue-plugin";
hljs.registerLanguage("javascript", javascript);
hljs.registerLanguage("css", css);
hljs.registerLanguage("xml", xml);
const { appContext: { app } } = getCurrentInstance();
app.use(ElementPlus);
app.use(hljsVuePlugin);
</script>

<style scoped>
@import "./node_modules/element-plus/dist/index.css";
@import "./node_modules/@highlightjs/cdn-assets/styles/stackoverflow-light.min.css";
</style>
