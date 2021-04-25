<template>
    <div class="home">
        <app-clock />
        <app-status />
    </div>
</template>

<script>
import AppClock from "../components/AppClock.vue";
import AppStatus from "../components/AppStatus.vue";
export default {
    components: {
        AppClock,
        AppStatus,
    },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Rubik&display=swap");
.home {
    font-family: "Rubik", sans-serif;
}
</style>
