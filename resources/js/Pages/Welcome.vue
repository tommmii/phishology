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


function sendPhish(){
    let phishingText = document.getElementById("phishingText").innerText;

}

</script>

<template>
    <Head title="Phishology" />
    <div class="bg-gray-50 text-black/50 dark:bg-black dark:text-white/50">
        <div
            class="relative flex min-h-screen flex-col items-center justify-center selection:bg-[#FF2D20] selection:text-white"
        >
            <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl">
                <header
                    class="items-center gap-2 py-10 lg:grid-cols-3"
                >
                    <div class="flex flex-col lg:col-start-2 lg:justify-center items-center text-lg text-black font-bold">
                        <span class="text-2xl">🐻 🍽️ 🐟</span>
                        <p>phishology</p>
                    </div>
                </header>

                <main class="mt-6">
                    <section class="grid grid-cols-2 text-black text-sm">
                        <div class="flex justify-end pr-10">
                            <div class="flex flex-col gap-1 w-1/2">
                                <p>Enter a message:</p>
                                <textarea class="bg-black/5 border-none rounded-md p-2 text-xs" id="phishingText"></textarea>
                                <button class="border-[1px] border-black/20 text-center p-1 rounded-md hover:bg-green-500/10 transition-all">🎣</button>
                            </div>
                        </div>
                        <div class="flex justify-start pl-10">
                            <div class="flex flex-col gap-1">
                                <div class="flex gap-2">
                                    <p>Are we going phishing?</p>
                                    <p class="font-bold text-sm uppercase"><span class="text-green-600">yes</span><span class="text-red-600">no</span></p>
                                </div>
                                <p class="text-xs">XX probability (%)</p>
                            </div>
                        </div>
                    </section>
                </main>

                <footer
                    class="py-16 text-center text-sm text-black dark:text-white/70"
                >
                    let's go spearphishing.
                </footer>
            </div>
        </div>
    </div>
</template>
