<template>
    <header class="flex items-center pb-10">
        <p class="text-sm">
            {{ `${xp.start} xp`}}
        </p>
        <div class="flex-1 h-1 mx-4 rounded-md lg:mx-6 bg-gray-line">
            <div class="relative h-1 bg-green" :style="{ width: `${currentXpPercentage}%` }">
                <p class="absolute text-sm -right-4 w-max top-2">
                    {{ `${xp.current} xp (${currentXpPercentage}%)` }}
                </p>
            </div>
        </div>
        <p class="text-sm">
            {{ `${xp.end} xp` }}
        </p>
    </header>
</template>

<script lang="ts">
import Vue from 'vue';
import { mapState, mapGetters } from 'vuex';

export default Vue.extend({
    computed: {
        ...mapState('Challenges', ['xp']),
        ...mapGetters('Challenges', ['currentXpPercentage'])
    }
})
</script>
