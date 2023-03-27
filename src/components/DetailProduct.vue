<template>
    <div type="button" @click="openModal">
        <figure class="flex flex-col items-center gap-y-2 lg:gap-y-6">
            <img
                :src="product.images[0]"
                alt="Juice Strawberry Flavor"
                width="170"
                class="aspect-[3/4] object-cover scale-90 lg:scale-100"
            />
            <figcaption class="flex flex-col items-center gap-y-1 lg:gap-y-2">
                <p class="text-xs">{{ titleCase(product.title) }}</p>
                <p class="font-bold text-xs">${{ product.price }}</p>
            </figcaption>
        </figure>
    </div>

    <TransitionRoot appear :show="isOpen" as="template">
        <Dialog as="div" @close="closeModal" class="relative z-10">
            <TransitionChild
                as="template"
                enter="duration-300 ease-out"
                enter-from="opacity-0"
                enter-to="opacity-160"
                leave="duration-200 ease-in"
                leave-from="opacity-160"
                leave-to="opacity-0"
            >
                <div class="fixed inset-0 bg-black bg-opacity-25" />
            </TransitionChild>

            <div class="fixed inset-0 overflow-y-auto">
                <div
                    class="flex min-h-full items-center justify-center p-4 text-center"
                >
                    <TransitionChild
                        as="template"
                        enter="duration-300 ease-out"
                        enter-from="opacity-0 scale-95"
                        enter-to="opacity-160 scale-160"
                        leave="duration-200 ease-in"
                        leave-from="opacity-160 scale-160"
                        leave-to="opacity-0 scale-95"
                    >
                        <DialogPanel
                            class="w-full max-w-5xl transform rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all relative"
                        >
                            <div class="flex flex-col lg:flex-row lg:gap-x-8">
                                <div
                                    class="flex flex-row order-1 lg:flex-col lg:gap-y-4"
                                >
                                    <div
                                        v-for="(image, index) in product.images"
                                        :key="index"
                                        class="flex items-center w-full my-8 lg:my-0"
                                    >
                                        <button
                                            :class="[
                                                imageSelected == index &&
                                                    'border border-black p-2',
                                            ]"
                                            type="button"
                                            @click="changeImageSelected(index)"
                                        >
                                            <img
                                                :src="image"
                                                alt="Juice Strawberry Flavor"
                                                class="aspect-[3/4] object-cover w-8 lg:w-[100px]"
                                            />
                                        </button>
                                    </div>
                                </div>
                                <div class="lg:order-2">
                                    <img
                                        :src="product.images[imageSelected]"
                                        alt="Juice Strawberry Flavor"
                                        width="1200"
                                        height="1200"
                                        class="aspect-square object-cover"
                                    />
                                </div>
                                <div
                                    class="w-full flex flex-col gap-y-4 lg:gap-y-10 order-2 lg:order-3"
                                >
                                    <div class="flex flex-col gap-y-2">
                                        <p>{{ titleCase(product.category) }}</p>
                                        <p class="text-3xl font-light">
                                            {{ titleCase(product.title) }}
                                        </p>
                                        <p>${{ product.price }}</p>
                                    </div>
                                    <div class="flex flex-col gap-y-4">
                                        <p>Quantity</p>
                                        <div class="flex items-center gap-x-4">
                                            <div
                                                class="flex items-center gap-x-6 px-4 py-2 bg-[#f1f0f0] rounded-lg w-fit"
                                            >
                                                <button
                                                    type="button"
                                                    @click="
                                                        count > 0 && count--
                                                    "
                                                >
                                                    -
                                                </button>
                                                <span>{{ count }}</span>
                                                <button
                                                    type="button"
                                                    @click="count++"
                                                >
                                                    +
                                                </button>
                                            </div>
                                            <button
                                                class="border border-black w-full rounded-full py-1.5"
                                                @click="
                                                    addCart(product),
                                                        closeModal()
                                                "
                                            >
                                                ADD TO CART
                                            </button>
                                        </div>
                                        <button
                                            class="w-full py-2 bg-black rounded-lg text-white"
                                            @click="
                                                addCart(product), closeModal()
                                            "
                                        >
                                            Buy it now
                                        </button>
                                    </div>
                                    <div
                                        class="flex items-center gap-x-6 my-2 border-b pt-2 pb-4 lg:my-0"
                                    >
                                        <div class="flex items-center gap-x-2">
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
                                                    d="M3 7.5L7.5 3m0 0L12 7.5M7.5 3v13.5m13.5 0L16.5 21m0 0L12 16.5m4.5 4.5V7.5"
                                                />
                                            </svg>
                                            <span>Compare</span>
                                        </div>
                                        <div class="flex items-center gap-x-2">
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
                                                    d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-9 5.25h.008v.008H12v-.008z"
                                                />
                                            </svg>
                                            <span>Ask a question</span>
                                        </div>
                                        <div class="flex items-center gap-x-2">
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
                                                    d="M7.217 10.907a2.25 2.25 0 100 2.186m0-2.186c.18.324.283.696.283 1.093s-.103.77-.283 1.093m0-2.186l9.566-5.314m-9.566 7.5l9.566 5.314m0 0a2.25 2.25 0 103.935 2.186 2.25 2.25 0 00-3.935-2.186zm0-12.814a2.25 2.25 0 103.933-2.185 2.25 2.25 0 00-3.933 2.185z"
                                                />
                                            </svg>
                                            <span>Share</span>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="absolute top-0 right-0">
                                <button
                                    type="button"
                                    class="inline-flex justify-center rounded-md border border-transparent bg-blue-160 px-4 py-2 text-sm font-medium text-blue-900 hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2"
                                    @click="closeModal"
                                >
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1"
                                        stroke="currentColor"
                                        class="w-10 h-10"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
                                        />
                                    </svg>
                                </button>
                            </div>
                            <div
                                class="mt-4 lg:mt-20 flex items-center pb-2 text-lg font-light justify-center gap-x-12 text-slate-400 relative"
                            >
                                <div>
                                    <p class="text-black">
                                        Product Description
                                    </p>
                                </div>
                                <div>
                                    <p>Shipping & Return</p>
                                </div>
                                <div>
                                    <p>Product Review</p>
                                </div>
                            </div>
                            <div class="border-t py-8 text-center">
                                <p>{{ product.description }}</p>
                            </div>
                        </DialogPanel>
                    </TransitionChild>
                </div>
            </div>
        </Dialog>
    </TransitionRoot>
</template>

<script setup>
import { ref } from "vue";
import {
    TransitionRoot,
    TransitionChild,
    Dialog,
    DialogPanel,
} from "@headlessui/vue";

const count = ref(0);
const isOpen = ref(false);
const imageSelected = ref(0);

function openModal() {
    isOpen.value = true;
    imageSelected.value = 0;
}

function closeModal() {
    isOpen.value = false;
}

function changeImageSelected(index) {
    imageSelected.value = index;
}

function titleCase(str) {
    var splitStr = str.replace("-", " ").toLowerCase().split(" ");
    for (var i = 0; i < splitStr.length; i++) {
        splitStr[i] =
            splitStr[i].charAt(0).toUpperCase() + splitStr[i].substring(1);
    }
    return splitStr.join(" ");
}
</script>

<script>
export default {
    props: ["product", "addCart", "deleteCart"],
};
</script>
