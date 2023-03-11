<script>
export default {
    data() {
        return {
            name: '',
            duration: 10,
        }
    },
    mounted() {
        this.$refs['name-input'].focus();
    },
}
</script>

<template>
    <form @submit.prevent="$emit('addBuff', name, duration)">
        <label>Name <input v-model="name" ref="name-input"/></label>
        <label>Duration <input v-model="duration" type="number"/></label>
        <button>OK</button>
    </form>
</template>

<style scoped>

</style>