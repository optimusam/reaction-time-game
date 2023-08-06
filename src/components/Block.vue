<template>
    <div class="block has-background-dark" v-if="show" @click="blockClicked">
        <p class="has-text-white">Click me!</p>
    </div>
</template>

<script>
    export default {
        name: 'Block',

        props: ['show'],

        updated() {
            this.startTime = Date.now();
        },

        data() {
            return {
                startTime: 0
            }
        },

        methods: {
            blockClicked() {
                const endTime = Date.now();
                const reactionTime = endTime - this.startTime;
                this.$emit('gameover', reactionTime);
            }
        }
    }
</script>

<style>

.block {
    height: 100%;
    width: 100%;
    padding: 50%;
    text-align: center;
    margin-top: 10%;
}
p {
    font-size: 30px;
}

</style>