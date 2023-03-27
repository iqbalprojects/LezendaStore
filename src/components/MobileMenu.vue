<template>
    <Popover class="relative">
        <PopoverButton>
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
                    d="M3.75 5.25h16.5m-16.5 4.5h16.5m-16.5 4.5h16.5m-16.5 4.5h16.5"
                />
            </svg>
        </PopoverButton>
        <PopoverPanel
            class="absolute right-0 top-9 z-10 bg-white border-2 border-slate-300 shadow-xl rounded-lg w-52 text-sm px-4 py-4 overflow-hidden"
        >
            <ul class="flex flex-col gap-y-4">
                <li class="border-b pb-1.5"><a href="">HOME</a></li>
                <li class="border-b pb-1.5"><a href="">SHOP</a></li>
                <li class="border-b pb-1.5"><a href="">PRODUCT</a></li>
                <li class="border-b pb-1.5"><a href="">PAGES</a></li>
                <li class="border-b pb-1.5"><a href="">BLOGS</a></li>
                <li class="border-b pb-1.5"><a href="">FEATURES</a></li>
            </ul>
        </PopoverPanel>
    </Popover>
</template>

<script setup>
import { Popover, PopoverButton, PopoverPanel } from "@headlessui/vue";
</script>
