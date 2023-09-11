
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

const checkToggle = () => {
    if (props.accept.value === true) {
        emits('turnOn');
    } else {
        emits('turnOff');
    }
}

</script>

<!-- const isToggled = ref(props.accept); -->
