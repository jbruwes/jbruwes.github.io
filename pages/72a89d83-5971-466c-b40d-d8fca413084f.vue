<template>
    <div class="container mx-auto px-4 overflow-hidden">
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
import { Icon } from "@iconify/vue";
hljs.registerLanguage("javascript", javascript);
hljs.registerLanguage("css", css);
hljs.registerLanguage("xml", xml);
const { appContext: { app } } = getCurrentInstance();
app.component("Icon", Icon);
app.use(ElementPlus);
app.use(hljsVuePlugin);
</script>


<style src="./node_modules/element-plus/dist/index.css"></style>
<style src="./node_modules/@highlightjs/cdn-assets/styles/stackoverflow-light.min.css"></style>
