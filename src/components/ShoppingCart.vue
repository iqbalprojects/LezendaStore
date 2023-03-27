<template>
    <PopoverPanel
        class="absolute -right-11 lg:-right-10 top- z-10 bg-white border-2 border-slate-300 shadow-xl rounded-lg w-96 h-max overflow-hidden"
    >
        <p class="p-6">Shopping Cart</p>
        <div class="flex flex-col justify-between gap-y-32">
            <ul class="flex flex-col gap-y-5 px-8">
                <div v-for="cart in carts" :key="cart.id">
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
                                <p class="text-sm text-slate-500">
                                    ${{ cart.price }}
                                </p>
                            </div>
                            <div class="flex items-center gap-x-4">
                                <div
                                    class="flex items-center gap-x-6 px-3 py-0.5 bg-[#f1f0f0] rounded-lg w-fit"
                                >
                                    <button
                                        type="button"
                                        @click="count > 0 && count--"
                                    >
                                        -
                                    </button>
                                    <span>{{ count }}</span>
                                    <button type="button" @click="count++">
                                        +
                                    </button>
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
                </div>
            </ul>
            <div class="bg-[#f7f6f6] py-4 px-6 border-t-2">
                <div class="flex items-center justify-around mb-5">
                    <span class="flex flex-col items-center">
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke-width="1.5"
                            stroke="currentColor"
                            class="w-6 h-6"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L6.832 19.82a4.5 4.5 0 01-1.897 1.13l-2.685.8.8-2.685a4.5 4.5 0 011.13-1.897L16.863 4.487zm0 0L19.5 7.125"
                            />
                        </svg>
                        <p>Note</p>
                    </span>
                    <span class="flex flex-col items-center">
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke-width="1.5"
                            stroke="currentColor"
                            class="w-6 h-6"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M8.25 18.75a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m3 0h6m-9 0H3.375a1.125 1.125 0 01-1.125-1.125V14.25m17.25 4.5a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m3 0h1.125c.621 0 1.129-.504 1.09-1.124a17.902 17.902 0 00-3.213-9.193 2.056 2.056 0 00-1.58-.86H14.25M16.5 18.75h-2.25m0-11.177v-.958c0-.568-.422-1.048-.987-1.106a48.554 48.554 0 00-10.026 0 1.106 1.106 0 00-.987 1.106v7.635m12-6.677v6.677m0 4.5v-4.5m0 0h-12"
                            />
                        </svg>
                        <p>Shipping</p>
                    </span>
                </div>
                <div class="flex items-center justify-between mb-4">
                    <p>Subtotal</p>
                    <p>Total Price</p>
                </div>
                <div class="flex flex-col items-center gap-y-2">
                    <button
                        class="w-full py-2 bg-black rounded-full text-white"
                    >
                        CHECK OUT
                    </button>
                    <p class="text-xs border-b border-black">View Cart</p>
                </div>
            </div>
        </div>
    </PopoverPanel>
</template>

<script setup>
import { PopoverPanel } from "@headlessui/vue";
import { ref } from "vue";

const count = ref(0);
</script>

<script>
export default {
    props: ["carts", "deleteCart"],
};
</script>
