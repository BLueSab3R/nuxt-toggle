
<template>
    <div @click="checkToggle">
        <slot></slot>
    </div>

    <RenderLess :accept="props.accept">
        {{ props.accept ? '1 on open male empty ' : '0 off closed female full ' }}
    </RenderLess>
</template>

<script setup>
import RenderLess from './RenderLess.vue';
const emits = defineEmits(['turnOn', 'turnOff'])
const props = defineProps({
    accept: {
        type: Boolean
    },
    type: {
        type: String
    },

});

const checkToggle = async () => {
    if (props.accept.value === true) {
        emits('turnOn');
        // try {
        //     const response = await fetch('https://api.example.com/start-service');
        //     console.log('Service started:', response.data);
        // } catch (error) {
        //     console.error('Error starting service:', error);
        // }
    } else {
        emits('turnOff');
        // try {
        //     const response = await fetch('https://api.example.com/stop-service');
        //     console.log('Service stopped:', response.data);
        // } catch (error) {
        //     console.error('Error stopping service:', error);
        // }
    }
}

</script>

<!-- const isToggled = ref(props.accept); -->

<!-- const asyncOnRequest = async () => {
    try {
        const response = await fetch('https://api.github.com');
        const data = await response.json();
        console.log(data);
        console.log('Async request:', data);
    } catch (error) {
        console.error('Error in request:', error);
    }
}
const asyncOffRequest = async () => {
    console.log('Async request off');
} -->
