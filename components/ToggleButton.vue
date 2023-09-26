
<template>
    <div @click="checkToggle">
        <slot></slot>
    </div>

    <RenderLess :accept="props.accept">
        {{ props.accept ? '1 on open male full' : '0 off closed female empty' }}
    </RenderLess>
</template>

<script setup>
import RenderLess from './RenderLess.vue';
const emits = defineEmits(['turnOn', 'turnOff'])
const props = defineProps({
    accept: {
        type: Boolean
    },
});

const checkToggle = async () => {
    if (props.accept === true) {
        emits('turnOff');
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/comments');
            const data = await response.json()
            console.log('Service stopped :', data);
        } catch (error) {
            console.error('Error starting service:', error);
        }
    } else {
        emits('turnOn');
        try {
            const response = await fetch('https://dog.ceo/api/breeds/list/all');
            const data = await response.json();
            console.log('Service started:', data);
        } catch (error) {
            console.error('Error stopping service:', error);
        }
    }   
}

</script>

