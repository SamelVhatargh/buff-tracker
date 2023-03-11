<script>
export default {
    data() {
        return {
            buffs: [
                {
                    name: 'Bless',
                    turns: {
                        total: 40,
                        left: 10,
                    },
                },
                {
                    name: 'Protection from Evil',
                    turns: {
                        total: 10,
                        left: 10,
                    },
                },
            ]
        }
    },
}
</script>

<template>
    <h1>Buffs</h1>
    <div v-for="buff in buffs">
        {{ buff.name }} {{buff.turns.left}}/{{buff.turns.total}}
    </div>
</template>

<style scoped>

</style>