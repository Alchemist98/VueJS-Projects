<template>
<div class="m-auto">
    <h1 class="font-bold text-2xl my-2 text-center">Vue Calendar</h1>
    <section class="mx-2 flex justify-between">
        <p class="font-bold">{{currentMonthName}}</p>
        <p class="font-bold">{{currentYear}}</p>
    </section>

    <section class="flex my-2">
        <p class="font-bold text-center" style="width: 14.28%" v-for="day in days" :key="day">{{ day }}</p>
    </section>

    <section class="flex flex-wrap">
        <p class="text-center" style="width: 14.28%" v-for="num in startDay()" :key="num"></p>
        <p class="font-bold text-center" style="width: 14.28%" v-for="num in daysInMonth()" :key="num" :class="currenDateClass(num)">{{ num }}</p>
    </section>

    <section class="flex justify-between my-5">
        <button class="px-2 border rounded" @click="prev">Prev</button>
        <button class="px-2 border rounded" @click="next">Next</button>
    </section>
</div>
</template>

<script>
export default {

    computed: {
        currentMonthName() {
            return new Date(this.currentYear, this.currentMonth).toLocaleDateString("default", {
                month: 'long'
            });
        },
    },

    methods: {
        daysInMonth() {
            return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
        },

        startDay() {
            return new Date(this.currentYear, this.currentMonth).getDay();
        },

        next() {
            if (this.currentMonth == 11) {
                this.currentMonth = 0;
                this.currentYear++;
            } else {
                this.currentMonth++;
            }

        },

        prev() {
            if (this.currentMonth == 0) {
                this.currentMonth = 11;
                this.currentYear--;
            } else {
                this.currentMonth--;
            }

        },

        currenDateClass(num) {
            const calenderFullDate = new Date(
                this.currentYear,
                this.currentMonth,
                num
            ).toDateString();
            const currentFullDate = new Date().toDateString();
            return calenderFullDate === currentFullDate ? "text-blue-600" : "";
        },
    },

    data() {
        return {
            currentDate: new Date().getUTCDate(),
            currentMonth: new Date().getMonth(),
            /**hi-IN */
            currentYear: new Date().getFullYear(),
            days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
        };

    },
};
</script>

<style>

</style>
