<template>
    <nav class="navbar-wrapper" :class="[{
        'navbar-fixed ': isHide,
    }]">
        <div class="navbar-logo">
            <img src="https://picsum.photos/200/300" alt="logo" />
        </div>
        <ul class="navbar-list">
            <li v-for="(item, index) in navLinks.navLinks" :key="index" class="nav-link">
                <nuxt-link class="navlink" :to="{ name: item.to }">
                    {{ item.name }}
                </nuxt-link>
            </li>
        </ul>
        <div class="navbar-right">
            <Icon @click="isOpenMobileMenu = !isOpenMobileMenu" class="mobile-menu-button" size="2em"
                style="color: black;margin-right: 15px;" name="ph:list"></Icon>
            <a href="#" class="navbar-tel">
                <span class="nabar-tel-icon">
                    <Icon style="color: white" name="ph:phone-call"></Icon>
                </span>
                <span>
                    {{ contact.phone }}
                </span>
            </a>
            <div class="navbar-button-wrapper">
                <button class="btn btn-primary rounded-pill">Zavolejte</button>
            </div>
        </div>
    </nav>
    <nav v-if="isOpenMobileMenu" class="mobile-nav-wrapper">
    </nav>
</template>
<script setup lang="ts">
import '@morev/vue-transitions/styles';
import { TransitionExpand } from '@morev/vue-transitions';

import navLinks from '~/assets/json/navlinks.json';
import contact from '~/assets/json/contact.json';
const { y } = useWindowScroll();
const isScrolling = ref(false);
const isHide = ref(false);
const isOpenMobileMenu = ref(false);
watchEffect(() => {
    if (y.value > 110) {
        isHide.value = true;
    } else {
        isHide.value = false;
    }
});
watchEffect(() => {
    if (y.value > 150) {
        isScrolling.value = true;
    } else {
        isScrolling.value = false;
    }
});

useHead({
    bodyAttrs: {
    },
})
</script>
<style lang="scss">
.open-mobile-menu {
    overflow-y: hidden;
}

.navbar-active-link {
    text-decoration: underline;
    text-underline-offset: 5px;
}

.mobile-menu-button {
    cursor: pointer;
}

.navbar-wrapper {
    display: flex;
    align-content: center;
    align-items: center;
    padding: 28px 70px 28px 70px;
    position: absolute;
    top: 0;
    width: 100%;
    height: 100px;
    transition: top 0.3s ease-in-out, position 0.3s ease-in-out;
    z-index: 5;

    .navbar-right {
        display: flex;
        margin-left: auto;
        align-items: center;

        .navbar-tel {
            display: flex;
            align-items: center;
            gap: 24px;
            font-weight: 500;
            margin-right: 15px;

            .nabar-tel-icon {
                background-color: #000000;
                width: 42px;
                height: 42px;
                display: grid;
                place-items: center;
                border-radius: 22px;
            }

            span {
                font-size: 22px;
            }
        }
    }

    .navbar-list {
        margin-bottom: 0;
        display: flex;
        gap: 32px;
        list-style: none;
        position: relative;

        .nav-link {
            a {
                text-decoration: none;
                color: black;
            }
        }
    }
}

.navbar-logo {
    width: 150px;
    height: 50px;
    margin-right: 4rem;

    img {
        width: 100%;
        height: 100%;
    }
}

.navlink {
    font-weight: 500;
    position: relative;
}

.navlink::after {
    content: "";
    background-color: black;
    position: absolute;
    bottom: -5px;
    left: 0;
    height: 2px;
    width: 0;
    transition: 0.2s;
}


.navlink:hover::after,
.navlink:focus::after {
    background-color: #000000;
    width: 100%;
}

.navbar-fixed {
    height: 80px;
    position: fixed;
    top: 0px;
    z-index: 5;
    background-color: white;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}

.mobile-nav-wrapper {
    position: fixed;
    width: 100%;
    height: 100%;
    background-color: black;
    z-index: 10;
}
</style>
<script setup>
</script>