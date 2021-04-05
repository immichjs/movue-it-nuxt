<template>
    <section class="flex flex-col items-center justify-center flex-1 px-10 py-6 md:px-16">
        <header class="w-full pb-6 border-b-2 border-background">
            <h2 class="text-xl font-semibold text-center text-blue">
                {{ `Ganhe ${amount} de experiência. `}}
            </h2>
        </header>
        <main class="flex flex-col items-center justify-center flex-1 mt-6">
            <img :src="`icons/${type}.svg`" :alt="type" :style="{ minHeight: '70px' }">
            <h1 class="mt-6 mb-2 text-3xl font-semibold text-title">
                Work Out (Mudar depois)
            </h1>
            <p class="text-base leading-6 text-center">
                {{ description }}
            </p>
        </main>
        <footer class="flex w-full gap-x-2">
            <button class="button failed" @click="resetChallenges">Falhar</button>
            <button class="button succeeded" @click="challengeSucceeded">Completar</button>
        </footer>
    </section>
</template>

<script lang="ts">
import Vue from 'vue'
import { mapState, mapMutations } from 'vuex';
import { Mutations as CountdownMT } from '~/store/Countdown/types';

import {
    Challenge as ChallengeType,
    Mutations as ChallengesMT,
} from '~/store/Challenges/types';

export default Vue.extend<unknown, any, unknown, ChallengeType>({
    props: {
        type: { type: String, required: true },
        description: { type: String, required: true },
        amount: { type: Number, required: true },
    },
    computed: mapState('Challenges', ['level', 'xp', 'completedChallenges']),
    methods: {
        ...mapMutations({
            resetTime: `Countdown/${CountdownMT.RESET_TIME}`,
            setIsActive: `Countdown/${CountdownMT.SET_IS_ACTIVE}`,
            setHasCompleted: `Countdown/${CountdownMT.SET_HAS_COMPLETED}`,
            setCurrentChallengeIndex: `Challenges/${ChallengesMT.SET_CURRENT_CHALLENGE_INDEX}`,
            completeChallenge: `Challenges/${ChallengesMT.COMPLETE_CHALLENGE}`
        }),
        resetChallenges () {
            this.resetTime();
            this.setIsActive(false);
            this.setHasCompleted(false);
            this.setCurrentChallengeIndex(null);
        },
        challengeSucceeded () {
            this.resetChallenges();
            this.completeChallenge(this.amount);

            this.$cookiz.set('movueit', {
                level: this.level,
                xp: this.xp,
                completedChallenges: this.completedChallenges,
            })
        }
    }
})
</script>
