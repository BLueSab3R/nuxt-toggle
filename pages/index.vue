<template>
    <div class='flex flex-col items-center justify-center h-screen'>
        <div class="bg-gray-200 rounded-md p-4">
            <select @change="optionHandler">
                <option value="null" disabled selected hidden>Choose option</option>
                <option value="simple"> Simple toggle</option>
                <option value="short">Short toggle</option>
                <option value="icon">Toggle with icon</option>
            </select>
        </div>
        <ToggleButton @turn-on="turnOn" @turn-off='turnOff' :counter='counter' :type="type" :accept="accept">
            <template v-if="type === 'simple'">
                <button type="button" :class="{
                    // 'bg-gray-200': !accept,
                    'bg-red-600': counter === 0,
                    'bg-yellow-200': counter === 1,
                    'bg-green-600': counter === 2,
                    // 'bg-indigo-600': accept,
                }"
                    class="mt-5 relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
                    role="switch" :aria-checked="!accept ? 'false' : 'true'">
                    <span class="sr-only">Use setting</span>
                    <span aria-hidden="true" :class="{
                        'translate-x-0': !accept,
                        'translate-x-5': accept,
                    }"
                        class='pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out'>
                    </span>

                </button>
            </template>
            <template v-if="type === 'short'">
                <button type="button"
                    class="mt-5 group relative inline-flex h-5 w-10 flex-shrink-0 cursor-pointer items-center justify-center rounded-full focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
                    role="switch" aria-checked="false">
                    <span class="sr-only">Use setting</span>
                    <span aria-hidden="true" class="pointer-events-none absolute h-full w-full rounded-md bg-white"></span>
                    <span aria-hidden="true" :class="{
                        // 'bg-gray-200': !accept,
                        // 'bg-indigo-600': accept,
                        'bg-red-600': counter === 0,
                        'bg-yellow-200': counter === 1,
                        'bg-green-600': counter === 2,
                    }"
                        class="pointer-events-none absolute mx-auto h-4 w-9 rounded-full transition-colors duration-200 ease-in-out"></span>
                    <span aria-hidden="true" :class="{
                        'translate-x-0': !accept,
                        'translate-x-5': accept,
                    }"
                        class="pointer-events-none absolute left-0 inline-block h-5 w-5 transform rounded-full border border-gray-200 bg-white shadow ring-0 transition-transform duration-200 ease-in-out"></span>

                </button>
            </template>
            <template v-if="type === 'icon'">
                <button type="button" :class="{
                    // 'bg-gray-200': !accept,
                    // 'bg-indigo-600': accept,
                    'bg-red-600': counter === 0,
                    'bg-yellow-200': counter === 1,
                    'bg-green-600': counter === 2,
                }"
                    class="mt-5 relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
                    role="switch" aria-checked="false">
                    <span class="sr-only">Use setting</span>
                    <span :class="{
                        'translate-x-0': !accept,
                        'translate-x-5': accept,
                    }" class="pointer-events-none relative inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0
              transition duration-200 ease-in-out">
                        <span :class="{
                            'opacity-100 duration-200 ease-in': !accept,
                            'opacity-100 duration-100 ease-out': accept,
                        }"
                            class="opacity-100 duration-200 ease-in absolute inset-0 flex h-full w-full items-center justify-center transition-opacity"
                            aria-hidden="true">
                            <svg class="h-3 w-3 text-gray-400" fill="none" viewBox="0 0 12 12">
                                <path d="M4 8l2-2m0 0l2-2M6 6L4 4m2 2l2 2" stroke="currentColor" stroke-width="2"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </svg>
                        </span>
                        <span
                            class="opacity-0 duration-100 ease-out absolute inset-0 flex h-full w-full items-center justify-center transition-opacity"
                            aria-hidden="true">
                            <svg class="h-3 w-3 text-indigo-600" fill="currentColor" viewBox="0 0 12 12">
                                <path
                                    d="M3.707 5.293a1 1 0 00-1.414 1.414l1.414-1.414zM5 8l-.707.707a1 1 0 001.414 0L5 8zm4.707-3.293a1 1 0 00-1.414-1.414l1.414 1.414zm-7.414 2l2 2 1.414-1.414-2-2-1.414 1.414zm3.414 2l4-4-1.414-1.414-4 4 1.414 1.414z" />
                            </svg>
                        </span>
                    </span>
                </button>
            </template>
        </ToggleButton>
    </div>
</template>
  
  
<script setup>
const type = ref(null);
const accept = ref(false);
let counter = ref(0);
const turnOn = () => {
    if (counter.value >= 2) {
        counter.value = 0;
    } else {
        counter.value++;

    }

    accept.value = !accept.value;
}

const turnOff = () => {
    if (counter.value >= 2) {
        counter.value = 0;
    } else {
        counter.value++;
    }
    accept.value = !accept.value;
}

const optionHandler = (event) => {
    type.value = event.target.value;
}

</script>


