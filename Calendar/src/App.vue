<template>
<AppHeader />
<div class="w-full flex">
    <Calendar />
</div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import Calendar from "./components/Calendar";
export default {
    components: {
        AppHeader,
        Calendar
    },
}
</script>

<style>

</style>
