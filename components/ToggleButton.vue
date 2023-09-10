
<template>
    <div @click="checkToggle">
        <slot></slot>
    </div>

    <RenderLess :isToggled="isToggled">
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

const isToggled = ref(props.accept);
const checkToggle = () => {
    if (isToggled.value === true) {
        emits('turnOn');
    } else {
        emits('turnOff');
    }
}

</script>

