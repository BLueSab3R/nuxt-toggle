<template >
    <template v-if="isToggled">
        <slot />


    </template>
    <template v-else>
        <slot />

    </template>
</template>

<script setup>
const emit = defineEmits(['toggleSwitch'])
const props = defineProps({
    isToggled: {
        type: Boolean
    }

});
watch(() => props.isToggled, (newValue) => {
    console.log('Змінено isToggled у RenderLess', newValue);
});

</script>


