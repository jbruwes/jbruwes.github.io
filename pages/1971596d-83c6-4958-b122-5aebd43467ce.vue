<template>
    <div class="my-4 "><el-text tag="b" size="large" class="!text-neutral-900">{{ the.title }}</el-text></div>
    <el-timeline>
        <el-timeline-item center :timestamp="new Date(lastmod).toLocaleDateString('ru-RU', options)" placement="top"
            v-for="{ title, description, lastmod, id, to } in the.$siblings.slice(2)" :key="id">
            <RouterLink :to="to">
                <el-card shadow="hover">
                    <el-text tag="b" size="large">{{ title }}</el-text>
                    <el-text tag="p">{{ description }}</el-text>
                </el-card>
            </RouterLink>
        </el-timeline-item>
    </el-timeline>
</template>

<script setup lang="js">
import { inject } from 'vue';
import { RouterLink } from 'vue-router';

const { id } = defineProps(["id"]),
    the = inject("pages")[id],
    options = { year: "numeric", month: "long", day: "numeric" };
</script>