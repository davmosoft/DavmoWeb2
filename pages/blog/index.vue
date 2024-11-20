<template>
    <section class="container">
        <div class="row text-center mb-5">
            <h1 class="page-heading mb-3">Blog</h1>
            <Icon size="24px" name="ph:caret-down-bold"></Icon>
        </div>
        <div class="row">
            <BlogItemGrid v-for="(item, index) in blogItems.blogData" :key="index" :title="item.title"
                :image="item.mainImg" :section="item.section" :date="item.date" :slug="item.slug">
            </BlogItemGrid>
        </div>
    </section>
</template>
<script setup lang="ts">
import blogJson from '~/assets/json/blog.json';
const blogItems = ref(blogJson);
</script>
<style lang="scss"></style>