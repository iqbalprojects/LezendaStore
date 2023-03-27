<template>
    <h2 class="mb-6 lg:8">
        Categories menu simplifies the product browsing process by providing a
        list of relevant categories for our users to choose from.
    </h2>
    <div class="mb-10 lg:hidden">
        <swiper
            :slidesPerView="'auto'"
            :spaceBetween="15"
            :freeMode="true"
            :pagination="false"
            :modules="modules"
            class="mySwiper"
        >
            <swiper-slide v-for="category in categories" :key="category.id">
                <figure>
                    <img
                        :src="category.thumbnail"
                        alt="Juice Strawberry Flavor"
                        class="rounded-lg aspect-[3/4] object-cover"
                    />
                    <figcaption class="text-center">
                        <p class="font-medium mt-4 mb-1">
                            {{ titleCase(category.category) }}
                        </p>
                        <p class="text-xs text-slate-500">
                            Try our convenient protein-packed smoothies!
                        </p>
                    </figcaption>
                </figure>
            </swiper-slide>
        </swiper>
    </div>
    <div class="hidden lg:grid lg:grid-cols-6 lg:gap-x-6 lg:mb-24">
        <figure v-for="category in categories" :key="category.id">
            <img
                :src="category.thumbnail"
                alt="Juice Strawberry Flavor"
                class="rounded-lg aspect-[3/4] object-cover"
            />
            <figcaption class="text-center">
                <p class="mt-5">
                    {{ titleCase(category.category) }}
                </p>
            </figcaption>
        </figure>
    </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/free-mode";
import "swiper/css/pagination";
import { FreeMode, Pagination } from "swiper";
import { ref, onMounted } from "vue";
import axios from "axios";

export default {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        const products = ref([]);
        const categories = ref([]);

        function titleCase(str) {
            var splitStr = str.replace("-", " ").toLowerCase().split(" ");
            for (var i = 0; i < splitStr.length; i++) {
                splitStr[i] =
                    splitStr[i].charAt(0).toUpperCase() +
                    splitStr[i].substring(1);
            }
            return splitStr.join(" ");
        }

        const getProducts = async () => {
            let response = await axios.get("https://dummyjson.com/products");
            products.value = response.data.products;
        };

        const getCategories = async () => {
            let response = await axios.get("https://dummyjson.com/products");
            categories.value = Array.from(
                new Set(
                    response.data.products.map((product) => product.category)
                )
            ).map((category) => {
                return response.data.products.find(
                    (product) => product.category === category
                );
            });
        };

        onMounted(() => {
            getProducts();
            getCategories();
        });

        return {
            products,
            categories,
            titleCase,
            modules: [FreeMode, Pagination],
        };
    },
};
</script>

<style>
.swiper-slide {
    width: 60%;
}
</style>
