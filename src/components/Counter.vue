<template>
    <section>
        <div  id="apps">
            <h1>Count Down To Event</h1>
        </div>
        <div  id="apps" v-if="!(countdown.dist < 0)">
            {{countdown.d}} Days {{countdown.h}} Hours {{countdown.m}} Minutes {{countdown.s}} Seconds 
        </div>
        <div v-else id="apps">
            17 b b f c 5 10 10 1d 1a 13 18 16 a 12 12 b d 1a 1e c a d 1a 12 17 a 11 b 11 9 1a d 1c 1a 13 11 1e f f 10
        </div>
    </section>
    <br>
    <br>
    <br>
    <br>
    
    <div class="counter">
        <button @click="subtract()">-</button>
        <pre>{{ count }}</pre>
        <button @click="add()">+</button>
    </div>
</template>

<script>

export default {
    data() {
        return {
            count: 0,
            countdown: {},
            countDownDate : new Date("Oct 3, 2022 00:00:00").getTime()
        }
    },
    methods: {
        add() {
            this.count += 1;
        },
        countdowner() {
                var now = new Date().getTime();

                // Find the distance between now and the count down date
                var distance = this.countDownDate - now;

                // Time calculations for days, hours, minutes and seconds
                var days = Math.floor(distance / (1000 * 60 * 60 * 24));
                var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                var seconds = Math.floor((distance % (1000 * 60)) / 1000);

                this.countdown = { d: days, h: hours, m: minutes, s:seconds, dist:distance}
            }
        },

    mounted() {
        setInterval(this.countdowner, 1000);
    },
};
</script>

<style>
.counter {
    display: grid;
    font-size: 2em;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    margin-top: 2em;
    place-items: center;
}

.counter-message {
    text-align: center;
    font-size: xx-large;
}#apps{
    font-size: xx-large;
    display: flex;
    justify-content: center;
}

</style>
