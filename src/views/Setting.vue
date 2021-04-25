<template>
    <div class="setting">
        <h2>Time (minutes)</h2>
        <div class="item">
            Focus <br />
            <input
                type="number"
                min="1"
                v-model="focusTime"
                @keyup.enter="save"
            />
        </div>
        <div class="item">
            Short break <br />
            <input
                type="number"
                min="1"
                v-model="shortBreakTime"
                @keyup.enter="save"
            />
        </div>
        <div class="item">
            Long break <br />
            <input
                type="number"
                min="1"
                v-model="longBreakTime"
                @keyup.enter="save"
            />
        </div>
        <button @click="save">OK</button>
    </div>
</template>

<script>
export default {
    name: "Setting",
    data() {
        return {
            focusTime: this.$store.state.settingData[0].time,
            shortBreakTime: this.$store.state.settingData[1].time,
            longBreakTime: this.$store.state.settingData[2].time,
        };
    },
    methods: {
        save() {
            this.$store.state.settingData[0].time = this.focusTime;
            this.$store.state.settingData[1].time = this.shortBreakTime;
            this.$store.state.settingData[2].time = this.longBreakTime;
        },
    },
};
</script>
<style lang="scss" scoped>
.setting {
    border-radius: 10px;
    width: 500px;
    height: 300px;
    display: block;
    position: relative;
    border: 2px solid #df645f;
    margin: auto;
    color: #df645f;
    .item {
        padding: 0px 20px;
        margin: 20px;
        color: #df645f;
        /* border: 2px solid; */
        input {
            border-radius: 5px;
            border: 2px solid #df645f;
        }
    }
}
button {
    color: white;
    border: none;
    margin: 0px 50px;
    background-color: #df645f;
    border-radius: 5px;
    font: {
        size: 13px;
        weight: bold;
    }
    padding: 10px 30px;
}
button:hover {
    cursor: pointer;
}
</style>
