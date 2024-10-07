<script setup>
import { Head } from '@inertiajs/vue3';
import { ref } from 'vue';


let probability = ref(0);
let hamOrSpam = ref('')
let beenPhished = ref(false);

async function sendPhish(){
    let phishingText = document.getElementById("phishingText").value;
    const predictData = await predictText(phishingText);
    probability.value = predictData.probability;
    hamOrSpam = predictData.label   
    if(probability.value >= .5){
        beenPhished=true;
    }

}

async function predictText(text, model = 'bert') {
  const url = 'https://europe.ots-api.telecomsxchange.com/predict/';
  
  const requestBody = {
    text: text,
    model: model
  };

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(requestBody)
    });

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const data = await response.json();
    return data;
  } catch (error) {
    console.error('There was a problem with the fetch operation:', error);
    throw error;
  }
}

</script>

<template>
    <Head title="Phishology" />
    <div class="bg-gray-50 text-black/50 dark:bg-black dark:text-white/50">
        <div
            class="relative flex min-h-screen flex-col items-center justify-center selection:bg-blue-400 selection:text-white"
        >
            <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl">
                <header
                    class="items-center gap-2 py-10 lg:grid-cols-3"
                >
                    <div class="flex flex-col lg:col-start-2 lg:justify-center items-center text-lg text-black font-bold">
                        <!-- <span class="text-2xl">🐻 🍽️ 🐟</span> -->
                        <img src="../../../public/images/logoImage.png" class=" w-20"/>
                        <p>phishology</p>
                    </div>
                </header>

                <main class="mt-6">
                    <section class="grid grid-cols-2 text-black text-sm">
                        <div class="flex justify-end pr-10">
                            <div class="flex flex-col gap-1  w-1/2">
                                <p>Enter a message:</p>
                                <textarea class="bg-black/5 border-none rounded-md p-2 text-xs min-h-10 max-h-52" id="phishingText"></textarea>
                                <button @click="sendPhish" class="border-[1px] border-black/20 text-center p-1 rounded-md hover:bg-blue-500/10 transition-all">🎣</button>
                            </div>
                        </div>
                        <div class="flex justify-start pl-10">
                            <div class="flex flex-col gap-1">
                                <div class="flex flex-col gap-1">
                                    <p>Are we hamming, spamming or phishin'?</p>
                                    <p class="font-bold text-sm uppercase" :class="{ 'text-green-600': hamOrSpam === 'ham', 'text-red-600': hamOrSpam === 'spam', 'text-blue-600': hamOrSpam === 'phishing' }">{{ hamOrSpam }} {{ hamOrSpam === 'phishing' ? '🎣' : '' }} {{ hamOrSpam === '' ? 'waiting' : '' }}</p>
                                </div>
                                <p class="text-xs"><span>{{((probability*100))}}</span>% probability</p>
                            </div>
                        </div>
                    </section>
                </main>

                <footer
                    class="py-16 text-center text-xs text-black dark:text-white/70"
                >
                    let's catch some phish.
                    <p class="pt-1">🐻 🍽️ 🐟</p>
                </footer>
            </div>
        </div>
    </div>
</template>
