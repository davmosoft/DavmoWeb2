<template>
    <footer class="footer-wrapper">
        <div class="container">
            <div class="row justify-content-center mb-5">
                <div class="col-lg-3">
                    <h5>
                        Kancelář
                    </h5>
                    <p>
                        Germany —
                        785 15h Street, Office 478
                        Berlin, De 81566
                    </p>
                    <a></a>
                </div>
                <div class="col-lg-3">
                    <h5>
                        Důležité odkazy
                    </h5>
                    <ul class="footer-list">
                        <li class="position-relative" v-for="(item, index) in navLinks.navLinks" :key="index">
                            <nuxt-link class="footerlink" :to="{ name: item.to }">{{ item.name }}</nuxt-link>
                        </li>
                    </ul>
                </div>
                <div class="col-lg-2">
                    <h5>
                        Sociální sítě
                    </h5>
                    <ul>
                        <li></li>
                    </ul>
                </div>
                <div class="col-lg-4">
                    <h5>
                        Newsletter
                    </h5>
                    <div class="position-relative d-flex">
                        <Icon class="icon-newsletter" name="ph:envelope-thin"></Icon>
                        <input type="email" class="input-newsletter" placeholder="Email" aria-label="Email"
                            aria-describedby="button-addon2">
                        <button class="btn-newsletter" type="button" id="button-addon2">
                            <Icon size="20px" style="color:white" name="ph:arrow-right-bold" />
                        </button>
                    </div>
                </div>
            </div>
            <hr class="divider" />
            <div class="row">
                <div class="col-lg-12">
                    <p>
                        © {{ currentYear }} <a href="#"> Davmosoft </a>
                    </p>
                </div>
            </div>
        </div>
    </footer>
</template>
<script setup lang="ts">
import navJson from '~/assets/json/navlinks.json'
const navLinks = ref(navJson)
const currentYear = new Date().getFullYear()
</script>
<style lang="scss">
.btn-newsletter {
    border: none;
    outline: none;
    background-color: #2562f4;
    width: 50px;
    height: 50px;
    border-radius: 50px;
    display: grid;
    place-items: center;
}

.input-newsletter {
    width: 100%;
    padding: 13px;
    padding-left: 52px;
    background: #191919;
    border-radius: 25px;
    border: none;
    caret-color: #f8f8f8;
    color: #f8f8f8;

    &:focus {
        outline: none;
    }
}

.icon-newsletter {
    position: absolute;
    top: 14px;
    left: 16px;
    color: #a2a2a2;
    font-size: 1.5em;
}

.divider {
    border-top: 1px solid #a2a2a2;
    margin-top: 24px;
    margin-bottom: 24px;
}

.footer-list {
    margin-top: 24px;

    li {
        color: #a2a2a2;
        margin-bottom: 24px;

        &:hover,
        :focus {
            color: #F8F8F8;
        }
    }
}

.footer-wrapper {
    h5 {
        color: #F8F8F8;
    }

    p {
        color: #a2a2a2;
    }
}

.footer-wrapper {
    padding-top: 120px;
    background-color: #0f0f0f;
    margin-top: 50px;
}

.footerlink {
    position: relative;
    transition: all 0.3s ease;
}

.footerlink::after {
    content: "";
    background-color: #F8F8F8;
    position: absolute;
    bottom: -5px;
    left: 0;
    height: 2px;
    width: 0;
    transition: 0.2s;
}

.footerlink:hover,
.footerlink:focus {
    transition: all 0.3s ease;
    color: #F8F8F8;
}

.footerlink:hover::after,
.footerlink:focus::after {
    background-color: #F8F8F8;
    width: 100%;
}
</style>