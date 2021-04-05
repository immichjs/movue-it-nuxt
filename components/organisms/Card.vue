<template>
    <div class="flex flex-1 w-full mt-8 bg-white rounded-md shadow-sm lg:mt-0">
        <Challenges v-if="currentChallenge" v-bind="currentChallenge"/>
        <StartCycle v-else />
        <LevelUpModal />
    </div>
</template>

<script lang="ts">
import Vue from 'vue';
import { mapGetters } from 'vuex';

import Challenges from '~/components/molecules/Challenges.vue';
import StartCycle from '~/components/atoms/StartCycle.vue';
import LevelUpModal from '~/components/atoms/LevelUpModal.vue';

export default Vue.extend({
    components: {
        Challenges,
        StartCycle,
        LevelUpModal,
    },
    computed: mapGetters('Challenges', ['currentChallenge'])
})
</script>
