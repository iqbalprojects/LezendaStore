<template>
    <div class="mb-10 lg:hidden">
        <swiper
            :slidesPerView="1"
            :pagination="false"
            :modules="modules"
            class="mySwiper"
        >
            <swiper-slide
                ><figure class="grid grid-cols-2">
                    <img
                        src="https://images.unsplash.com/photo-1524638088-758d9961fc6f"
                        alt=""
                        class="w-40 h-44"
                    />
                    <figcaption class="flex flex-col justify-around">
                        <p class="text-xl">Create your pack</p>
                        <p class="text-xs text-slate-500">
                            Get a special offer on your first box. FREE SHIPPING
                            all the time.
                        </p>
                        <a
                            class="text-xs border-b-2 border-black pb-1 w-fit"
                            href="http://"
                            >SHOP NOW</a
                        >
                    </figcaption>
                </figure></swiper-slide
            >
            <swiper-slide
                ><figure class="grid grid-cols-2 gap-x-4">
                    <img
                        src="https://images.unsplash.com/photo-1519627457373-b60a0da1706b"
                        alt=""
                        class="w-40 h-44 object-cover"
                    />
                    <figcaption class="flex flex-col justify-evenly">
                        <p class="text-xl">100% fruit, 0% anything else</p>
                        <p class="text-xs text-slate-500">
                            A fruit gives healthy mind but a fruit juice gives
                            you healthy body too
                        </p>
                        <a
                            class="text-xs border-b-2 border-black pb-1 w-fit"
                            href="http://"
                            >WHAT MAKES US DIFFERENT</a
                        >
                    </figcaption>
                </figure></swiper-slide
            >
        </swiper>
    </div>
    <div class="hidden lg:grid lg:grid-cols-2 lg:gap-10 lg:mb-24">
        <figure class="grid grid-cols-2 gap-16">
            <img
                src="https://images.unsplash.com/photo-1524638088-758d9961fc6f"
                alt=""
                class="aspect-[3/4] object-cover"
            />
            <figcaption class="flex flex-col justify-around">
                <p class="text-xl">Create your pack</p>
                <p class="text-xs text-slate-500">
                    Get a special offer on your first box. FREE SHIPPING all the
                    time.
                </p>
                <a
                    class="text-xs border-b-2 border-black pb-1 w-fit"
                    href="http://"
                    >SHOP NOW</a
                >
            </figcaption>
        </figure>
        <figure class="grid grid-cols-2 gap-16">
            <img
                src="https://images.unsplash.com/photo-1519627457373-b60a0da1706b"
                alt=""
                class="aspect-[3/4]"
            />
            <figcaption class="flex flex-col justify-around">
                <p class="text-xl">100% fruit, 0% anything else</p>
                <p class="text-xs text-slate-500">
                    A fruit gives healthy mind but a fruit juice gives you
                    healthy body too
                </p>
                <a
                    class="text-xs border-b-2 border-black pb-1 w-fit"
                    href="http://"
                    >WHAT MAKES US DIFFERENT</a
                >
            </figcaption>
        </figure>
    </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import { Pagination } from "swiper";

export default {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        return {
            modules: [Pagination],
        };
    },
};
</script>
