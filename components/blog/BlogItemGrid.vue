<template>
    <article class="col-lg-4 col-md-6 col-sm-12 col-12">
        <div class="item-image">
            <nuxt-link :to="{ name: 'blog-slug', params: { slug: props.slug } }"><img src="https://picsum.photos/500"
                    alt="Blog Image" /></nuxt-link>
        </div>
        <div class="item-info">
            <span class="item-section">
                {{ props.section }}
            </span>
            <span class="item-date">
                {{ props.date }}
            </span>
        </div>
        <div class="item-content">
            <nuxt-link :to="{ name: 'blog-slug', params: { slug: props.slug } }">
                <h2>
                    {{ props.title }}
                </h2>
            </nuxt-link>
        </div>
    </article>
</template>
<script setup lang="ts">
const props = defineProps<{
    title: string;
    date: string;
    section: string;
    image?: string;
    slug: string;
}>();
</script>
<style lang="scss">
.item-content {
    h2 {
        font-size: 28px;
        font-weight: 600;
    }
}

.item-info {
    margin: 12px 0px;
    display: flex;
    gap: 26px;

    .item-section {
        font-size: 14px;
        position: relative;

        &::after {
            content: "";
            position: absolute;
            display: inline-block;
            width: 4px;
            height: 4px;
            top: 9px;
            right: -16px;
            background-color: #969696;
            border-radius: 50%;

        }
    }

    .item-date {
        font-size: 14px;
        font-weight: 300;
        color: #969696;
    }
}

.item-image {
    overflow: hidden;
    border-radius: 15px;

    img {
        height: 300px;
        width: 100%;
        object-fit: cover;
        transition: all 0.4s ease;

        &:hover {
            transform: scale(1.05);
            transition: all 0.4s ease;
        }
    }
}
</style>