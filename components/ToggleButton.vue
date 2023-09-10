
<template>
    <div>
        <slot></slot>
    </div>

    <RenderLess :isToggled="isToggled">
        {{ isToggled ? '1 on open male empty ' : '0 off closed female full ' }}
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
    },

});

const isToggled = ref(props.accept);

const toggleSwitch = () => {
    isToggled.value = !isToggled.value;

}
</script>

