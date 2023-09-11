
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
        try {
            const response = await fetch('https://api.example.com/start-service');
            console.log('Service started:', response.data);
        } catch (error) {
            console.error('Error starting service:', error);
        }
    } else {
        emits('turnOff');
        try {
            const response = await fetch('https://api.example.com/stop-service');
            console.log('Service stopped:', response.data);
        } catch (error) {
            console.error('Error stopping service:', error);
        }
    }
}

</script>

