<template>
    <section class="container">
        <div class="row">
            <div class="badge"></div>
            <h1 class="page-heading text-center">{{ blogDetail.title }}
            </h1>
            <div class="item-info justify-content-center d-flex">
                <span class="item-date">{{ blogDetail.date }}</span>
            </div>
        </div>
        <div class="blog-container">
            <div class="blog-img">
                <img :src="blogDetail.mainImg" />
            </div>
            <div class="d-flex justify-content-center ">
                <div class="col-6 blog-content">
                    <p>At vero eos et accusam
                        Sed ut perspiciatis, unde omnis iste natus error sit voluptatem accusantium doloremque
                        laudantium, totam rem aperiam eaque ipsa, quae ab illo inventore veritatis et quasi architecto
                        beatae vitae dicta sunt.</p>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup lang="ts">
import type { BlogItem } from '~/models/blogItem';
import blogJson from '~/assets/json/blog.json';
const route = useRoute();
const blogDetail = ref<BlogItem>({ title: '', date: '', mainImg: '', section: '', slug: '' });
onMounted(() => {
    const blog = blogJson.blogData.find((item) => item.slug === route.params.slug);
    if (blog) {
        blogDetail.value = blog;
    }
});

</script>
<style lang="scss">
.blog-container {
    margin-top: 15px;
}
.blog-content {
    p {
        font-weight: 400;
        color: #696969;
    }
}
.blog-img {
    margin-bottom: 50px;
    height: 600px;
    img {
        border-radius: 15px;
    }
}
</style>