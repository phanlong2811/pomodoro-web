<template>
    <div class="clock">
        <h1>{{ tittle }}</h1>
        <h2>{{ time }}</h2>
        <button @click="clickFunction">{{ buttonTitle }}</button>
    </div>
</template>

<script>
export default {
    name: "Home",
    components: {},
    watch: {
        seconds(val) {
            if (val == 0 && this.minutes == 0) {
                this.pause();
                this.id = (this.id + 1) % 3;
            }
        },
        id(val) {
            this.minutes = this.$store.state.settingData[val].time;
            this.seconds = 0;
        },
    },
    computed: {
        time() {
            return (
                (this.minutes < 10 ? "0" : "") +
                this.minutes +
                " : " +
                (this.seconds < 10 ? "0" : "") +
                this.seconds
            );
        },
        buttonTitle() {
            return this.isPause ? "START" : "PAUSE";
        },
        tittle() {
            return this.nameTitle[this.id];
        },
    },
    data() {
        return {
            id: 0,
            nameTitle: ["Focus", "Short Beark", "Long Break"],
            minutes: this.$store.state.settingData[0].time,
            seconds: 0,
            isPause: true,
        };
    },
    methods: {
        async clickFunction() {
            if (this.isPause) this.start();
            else this.pause();
        },
        async start() {
            this.isPause = false;
            this.countTime();
        },
        async pause() {
            this.isPause = true;
        },
        async countTime() {
            if (!this.isPause) {
                var handle = setInterval(() => {
                    if ((!this.minutes && !this.seconds) || this.isPause) {
                        clearInterval(handle);
                        this.pause();
                    } else {
                        if (this.seconds == 0 && this.minutes > 0) {
                            this.seconds = 59;
                            this.minutes--;
                        } else this.seconds--;
                    }
                }, 1000);
            }
        },
    },
};
</script>

<style lang="scss" scoped>
h1 {
    font-size: 30px;
    margin: 0px;
}
h2 {
    font-size: 100px;
    margin: 40px;
}
.clock {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    display: block;
    position: relative;
    width: 500px;
    height: 300px;
    background: {
        color: #df645f;
    }
    border-radius: 20px;
    padding: 50px;
    margin: auto;
    color: white;
}
button {
    background: {
        color: white;
    }
    color: #df645f;
    border-radius: 10px;
    padding: 15px 32px;
    border: none;
    width: 200px;
    height: 70px;
    text : {
        align: center;
        decoration: none;
    }
    cursor: pointer;
    display: inline-block;
    font: {
        size: 25px;
        weight: bold;
    }
}
</style>
