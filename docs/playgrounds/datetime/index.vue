<template>
    <div class="demo py-[40px] px-[64px]">

        <!-- Title -->
        <h1 class="text-[32px] font-semibold leading-snug -tracking-[.7px] mb-12">
            DateTime - Playground
        </h1>

        <!-- Heading -->
        <h2 class="font-semibold mb-6">
            Date (between 2010 and 2030)
        </h2>

        <!-- Date -->
        <v-datetime type="date"
                    v-model="date"
                    label="Start date"
                    minDate="2010-02-05"
                    maxDate="2030-11-12"
                    icon="fas fa-calendar">
        </v-datetime>

        <!-- Heading -->
        <h2 class="font-semibold my-6">
            Time (24 hour)
        </h2>

        <!-- Time -->
        <v-datetime type="time"
                    v-model="time"
                    label="Start time"
                    icon="fas fa-clock">
        </v-datetime>

        <!-- Heading -->
        <h2 class="font-semibold my-6">
            DateTime (with meridiem hint)
        </h2>

        <!-- DateTime -->
        <v-datetime type="datetime"
                    :meridiem="true"
                    v-model="datetime"
                    :showSeconds="true"
                    icon="fas fa-calendar"
                    label="Start date / time">
        </v-datetime>

    </div>
</template>

<script>
    import DateTimeComponent from '../../../src/components/datetime.vue';

    export default
    {
        components : {
            'v-datetime' : DateTimeComponent,
        },

        data() {
            return {
                date     : '2022-08-10',
                time     : '16:35:22.000Z',
                datetime : '2022-09-10T16:35:12.000Z',
            }
        },
    }
</script>