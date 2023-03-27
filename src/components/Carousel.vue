<template>
    <div class="mb-10 bg-gradient-to-r from-[#e9c592] to-[#cba071]">
        <swiper :pagination="true" :modules="modules" class="mySwiper">
            <swiper-slide><Hero /></swiper-slide>
            <swiper-slide><Hero /></swiper-slide>
            <swiper-slide><Hero /></swiper-slide>
        </swiper>
    </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import { Pagination } from "swiper";
import Hero from "./Hero.vue";

export default {
    components: {
        Swiper,
        SwiperSlide,
        Hero,
    },
    setup() {
        return {
            modules: [Pagination],
        };
    },
};
</script>
