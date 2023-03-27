<template>
    <Navbar :carts="carts" :deleteCart="deleteCart" />
    <Carousel />
    <div class="container mx-auto px-3 lg:px-0">
        <BestSeller :addCart="addCart" />
        <Category />
        <Overage />
    </div>
    <ShotBundle />
    <Gallery />
    <Footer />
</template>

<script setup>
import Navbar from "./../components/Navbar.vue";
import Carousel from "./../components/Carousel.vue";
import BestSeller from "../components/BestSeller.vue";
import Category from "./../components/Category.vue";
import Overage from "./../components/Overage.vue";
import ShotBundle from "./../components/ShotBundle.vue";
import Gallery from "./../components/Gallery.vue";
import Footer from "./../components/Footer.vue";
import { ref } from "vue";

const carts = ref([]);

function addCart(product) {
    const cartArr = carts.value;
    carts.value = [...cartArr, product];
}

function deleteCart(product) {
    carts.value = carts.value.filter((data) => data.id != product.id);
}
</script>

<script>
export default {
    setup() {
        return { carts };
    },
};
</script>
