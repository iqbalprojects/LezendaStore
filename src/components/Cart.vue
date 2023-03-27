<template>
    <li class="flex gap-x-8">
        <img
            :src="cart.images[0]"
            alt="Juice Passion Flavor"
            width="100"
            class="border border-slate-300 aspect-square object-cover"
        />
        <div class="flex flex-col justify-between">
            <div class="flex flex-col gap-y-0.5">
                <p>{{ cart.title }}</p>
                <p class="text-sm text-slate-500">${{ cart.price }}</p>
            </div>
            <div class="flex items-center gap-x-4">
                <div
                    class="flex items-center gap-x-6 px-3 py-0.5 bg-[#f1f0f0] rounded-lg w-fit"
                >
                    <button type="button" @click="count > 0 && count--">
                        -
                    </button>
                    <span>{{ count }}</span>
                    <button type="button" @click="count++">+</button>
                </div>
                <p
                    class="text-xs border-b border-black"
                    @click="deleteCart(cart)"
                >
                    Remove
                </p>
            </div>
        </div>
    </li>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);
</script>

<script>
export default {
    props: ["cart", "deleteCart"],
};
</script>
