<script>
import BuffForm from "@/components/BuffForm.vue";

export default {
    components: {BuffForm},
    data() {
        return {
            showBuffForm: false,
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
    methods: {
        addBuff(name, duration) {
            this.buffs.push({
                name: name,
                turns: {
                    total: duration,
                    left: duration,
                }
            });
            this.showBuffForm = false;
        }
    }
}
</script>

<template>
    <h1>Buffs</h1>
    <button @click="showBuffForm = !showBuffForm">Add</button>
    <BuffForm v-if="showBuffForm" @add-buff="addBuff" />
    <div v-for="buff in buffs">
        {{ buff.name }} {{buff.turns.left}}/{{buff.turns.total}}
    </div>
</template>

<style scoped>

</style>