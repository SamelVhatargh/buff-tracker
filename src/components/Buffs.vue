<script>
import BuffForm from "@/components/BuffForm.vue";

export default {
    components: {BuffForm},
    data() {
        return {
            showBuffForm: false,
            buffs: [],
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
        },
        nextTurn() {
            for (let i = 0; i < this.buffs.length; i++) {
                let buff = this.buffs[i];
                buff.turns.left--;
            }
        },
        clear() {
            this.buffs = [];
            this.showBuffForm = false;
        },
        removeBuff(id) {
            this.buffs.splice(id, 1);
        }
    },
    mounted() {
        this._keyListener = function(e) {
            if (e.key === "n" && e.ctrlKey && e.altKey) {
                this.nextTurn();
            }
            if (e.key === "a" && e.ctrlKey && e.altKey) {
                this.showBuffForm = !this.showBuffForm;
            }
        };

        document.addEventListener('keydown', this._keyListener.bind(this));
    },
    beforeDestroy() {
        document.removeEventListener('keydown', this._keyListener);
    }
}
</script>

<template>
    <h1>Buffs</h1>
    <button @click="clear">Clear</button>
    <button @click="nextTurn">Next Turn</button>
    <button @click="showBuffForm = !showBuffForm">Add</button>
    <BuffForm v-if="showBuffForm" @add-buff="addBuff" />
    <h2>Active</h2>
    <table>
        <template  v-for="(buff, id) in buffs">
            <tr v-if="buff.turns.left > 0">
                <td>{{ buff.name }}</td>
                <td>{{ buff.turns.left }}/{{ buff.turns.total }}</td>
                <td @click="removeBuff(id)"> X</td>
            </tr>
        </template>
    </table>

    <h2>Past</h2>
    <table>
        <template v-for="(buff, id) in buffs">
            <tr v-if="buff.turns.left <= 0">
                <td>{{ buff.name }}</td>
                <td @click="removeBuff(id)"> X</td>
            </tr>
        </template>
    </table>
    <h3>Shortcuts</h3>
    <ul>
        <li>Ctrl+Alt+N - Next Turn</li>
        <li>Ctrl+Alt+A - Add Buff</li>
    </ul>
</template>

<style scoped>

</style>