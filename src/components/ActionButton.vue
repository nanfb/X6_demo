<template>
    <div>
        <button @click="action('')">上一步</button>
        <button @click="action('')">下一步</button>
        <button @click="action('')">清空画布</button>
        <button @click="action('')">放大</button>
        <button @click="action('')">缩小</button>
        <button @click="action('')">回中点</button>
    </div>
</template>

<script>
export default {
    name: 'ActionButton',
    data() {
        return {

        }
    },
    methods: {
        action(type) {
            this.$emit('action', type)
        }
    }
}
</script>
<style></style>