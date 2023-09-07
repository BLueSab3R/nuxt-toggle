<template>
    <div>
        <button v-if="type === 'simple'" type="button" @click="toggleSwitch" :class="{
            'bg-gray-200': !isToggled,
            'bg-indigo-600': isToggled,
        }"
            class="mt-5 relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
            role="switch" :aria-checked="!isToggled ? 'false' : 'true'">
            <span class="sr-only">Use setting</span>
            <span aria-hidden="true" :class="{
                'translate-x-0': !isToggled,
                'translate-x-5': isToggled,
            }"
                class='pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out'>
            </span>

        </button>
    </div>


    <button v-if="type === 'short'" type="button" @click="toggleSwitch"
        class="mt-5 group relative inline-flex h-5 w-10 flex-shrink-0 cursor-pointer items-center justify-center rounded-full focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
        role="switch" aria-checked="false">
        <span class="sr-only">Use setting</span>
        <span aria-hidden="true" class="pointer-events-none absolute h-full w-full rounded-md bg-white"></span>
        <span aria-hidden="true" :class="{ 'bg-gray-200': !isToggled, 'bg-indigo-600': isToggled }"
            class="pointer-events-none absolute mx-auto h-4 w-9 rounded-full transition-colors duration-200 ease-in-out"></span>
        <span aria-hidden="true" :class="{
            'translate-x-0': !isToggled,
            'translate-x-5': isToggled,
        }"
            class="pointer-events-none absolute left-0 inline-block h-5 w-5 transform rounded-full border border-gray-200 bg-white shadow ring-0 transition-transform duration-200 ease-in-out"></span>

    </button>



    <button v-if="type === 'icon'" type="button" @click="toggleSwitch"
        :class="{ 'bg-gray-200': !isToggled, 'bg-indigo-600': isToggled }"
        class="mt-5 relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
        role="switch" aria-checked="false">
        <span class="sr-only">Use setting</span>
        <span :class="{
            'translate-x-0': !isToggled,
            'translate-x-5': isToggled,
        }" class="pointer-events-none relative inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0
              transition duration-200 ease-in-out">
            <span :class="{
                'opacity-100 duration-200 ease-in': !isToggled,
                'opacity-100 duration-100 ease-out': isToggled,
            }"
                class="opacity-100 duration-200 ease-in absolute inset-0 flex h-full w-full items-center justify-center transition-opacity"
                aria-hidden="true">
                <svg class="h-3 w-3 text-gray-400" fill="none" viewBox="0 0 12 12">
                    <path d="M4 8l2-2m0 0l2-2M6 6L4 4m2 2l2 2" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                        stroke-linejoin="round" />
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
    <RenderLess :isToggled="isToggled" @toggle-switch="toggleSwitch" v-slot="message">
        {{ message.message }}
    </RenderLess>
</template>

<script setup>
import RenderLess from './RenderLess.vue';
const props = defineProps({
    accept: {
        type: Boolean
    },
    type: {
        type: String
    }
});

const isToggled = ref(props.accept);

const toggleSwitch = () => {
    isToggled.value = !isToggled.value;
}
</script>

