<script>
export default {
    data() {
        return {
            name: '',
            duration: 0,
        }
    }
}
</script>

<template>
    <div>
        <label>Name <input v-model="name"/></label>
        <label>Duration <input v-model="duration" type="number"/></label>
        <button @click="$emit('addBuff', name, duration)">OK</button>
    </div>
</template>

<style scoped>

</style>