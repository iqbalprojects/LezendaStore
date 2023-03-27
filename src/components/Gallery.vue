<template>
    <div class="text-center mb-8 flex flex-col items-center gap-y-3">
        <p>Follow us on instagram</p>
        <p class="text-xs">@lezenda</p>
    </div>
    <div class="grid grid-cols-2 gap-4 px-3 mb-16 lg:flex">
        <div v-for="(photo, index) in photos" :key="index">
            <img :src="photo" alt="" class="aspect-square object-cover" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            photos: [
                "https://source.unsplash.com/random/?shop&1",
                "https://source.unsplash.com/random/?shop&2",
                "https://source.unsplash.com/random/?shop&3",
                "https://source.unsplash.com/random/?shop&4",
                "https://source.unsplash.com/random/?shop&5",
                "https://source.unsplash.com/random/?shop&6",
            ],
        };
    },
};
</script>
