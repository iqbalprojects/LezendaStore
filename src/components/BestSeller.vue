<template>
    <div>
        <h2 class="mb-8">Our Best Sellers</h2>
        <div
            class="mb-10 grid grid-cols-2 items-center gap-y-8 gap-x-3 lg:grid-flow-col lg:grid-cols-none lg:gap-x-0 lg:mb-24"
        >
            <div
                v-for="product in products.filter(
                    (data) =>
                        data.id == 2 ||
                        data.id == 19 ||
                        data.id == 23 ||
                        data.id == 24
                )"
            >
                <DetailProduct :product="product" :addCart="addCart" />
            </div>
        </div>
    </div>
</template>
<script setup>
import DetailProduct from "./DetailProduct.vue";
import { ref, onMounted } from "vue";
import axios from "axios";

const products = ref([]);

async function getProducts() {
    let response = await axios.get("https://dummyjson.com/products");
    products.value = response.data.products;
}

onMounted(() => {
    getProducts();
});
</script>

<script>
export default {
    setup() {
        return { products };
    },
    props: ["addCart"],
};
</script>
