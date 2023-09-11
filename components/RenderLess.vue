<template >
    <template v-if="props.accept">
        <slot />


    </template>
    <template v-else>
        <slot />

    </template>
</template>

<script setup>
const props = defineProps({
    accept: {
        type: Boolean
    }

});
watch(() => props.accept, (newValue) => {
    console.log('Змінено props.accept у RenderLess', newValue);
});

</script>


