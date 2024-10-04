<script setup>
import { Head } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

</script>

<template>
    <Head title="Phishology" />
    <div class="bg-gray-50 text-black/50 dark:bg-black dark:text-white/50">
        <div
            class="relative flex min-h-screen flex-col items-center justify-center selection:bg-[#FF2D20] selection:text-white"
        >
            <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl">
                <header
                    class="grid grid-cols-2 items-center gap-2 py-10 lg:grid-cols-3"
                >
                    <div class="flex flex-col lg:col-start-2 lg:justify-center items-center text-lg text-black font-bold">
                        <span class="text-2xl">🐻 🍽️ 🐟</span>
                        <p>phishology</p>
                    </div>
                </header>

                <main class="mt-6">
                    <section class="grid grid-cols-2">
                        <div class="flex justify-center">
                            <p>text input</p>
                        </div>
                        <div class="flex justify-center">
                            <p>probability output</p>
                        </div>
                    </section>
                </main>

                <footer
                    class="py-16 text-center text-sm text-black dark:text-white/70"
                >
                    spearphishing.
                </footer>
            </div>
        </div>
    </div>
</template>
