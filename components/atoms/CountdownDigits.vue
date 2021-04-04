<template>
    <p class="flex w-1/2 gap-x-1">
        <span v-for="(digit, index) in splittedDigits" :key="index" class="flex items-center justify-center w-1/2 py-3 bg-white rounded-md">
            {{ digit }}
        </span>
    </p>
</template>

<script lang="ts">
import Vue from 'vue';
import { splitValue } from '~/utils';

export default Vue.extend({
    props: {
        digits: { type: Number, required: true },
    },
    computed: {
        splittedDigits (): string[] {
            return splitValue(this.digits);
        },
    }
})
</script>
