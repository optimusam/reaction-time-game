<template>
    <div class="result" v-if="show">
        <p>Your reaction time is {{ reactionTime }}ms </p>
        <p>{{ showMessage(reactionTime) }}</p>
    </div>
</template>

<script>

    export default {
        name: 'Result',
        props: ['reactionTime', 'show'],
        methods: {
            showMessage(reactionTime) {
                if(reactionTime < 200)
                    return "Fast as Flash ⚡️";
                else if(reactionTime >= 200 && reactionTime <= 400) 
                    return "Good Timing! 🫡";
                else 
                    return "Snail pace 🐌";
            }
        }
    }

</script>