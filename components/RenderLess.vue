<template >
    <template v-if="isToggled">
        <slot @click="()=>console.log('111111111111111111111')" message='1 ' />
        <slot message='off ' />
        <slot message='closed ' />
        <slot message='female ' />
        <slot message='full ' />

    </template>
    <template v-else>
        <slot message='0 ' />
        <slot message='on ' />
        <slot message='open ' />
        <slot message='male ' />
        <slot message='empty ' />
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
const toggleSwitch = () => {
    isToggled.value = !isToggled.value;
}
</script>
<script>
export default {
    methods: {
        toggleSwitch() {
            this.$emit(isToggled.value = !isToggled.value);
        },
    },
};
</script>

