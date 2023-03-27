<template>
    <div class="lg:flex lg:flex-row lg:items-center lg:justify-between px-8">
        <div
            class="py-16 text-center lg:px-4 lg:py-20 lg:text-start lg:max-w-xl"
        >
            <p class="text-xl mx-auto lg:mx-0 lg:text-2xl lg:font-medium">
                Shop the World at Your Fingertips
            </p>
            <p
                class="text-xs text-slate-500 my-6 mx-auto lg:mx-0 lg:text-base lg:leading-8"
            >
                Shop conveniently from a variety of categories, including
                electronics, fashion, home, and more, all in one place.
            </p>
            <button
                class="text-sm font-semibold px-6 py-2 border border-black rounded-full"
            >
                SHOP NOW
            </button>
        </div>
        <div class="hidden lg:block">
            <lottie-player
                autoplay
                loop
                mode="normal"
                src="https://assets9.lottiefiles.com/packages/lf20_2gu7eqwz.json"
                class="lg:w-96"
            >
            </lottie-player>
        </div>
    </div>
</template>

<script>
import * as LottiePlayer from "@lottiefiles/lottie-player";
</script>
