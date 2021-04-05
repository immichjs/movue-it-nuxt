<template>
    <transition name="slide-fade">
        <div
            v-if="isLevelUpModalOpen"
            class="fixed inset-0 flex items-center justify-center overlay bg-gray-line"
            @click="setModalState(false)"
        >
            <div class="relative w-full max-w-md p-10 text-center bg-white rounded-md shadow-lg" @click.stop>
                <header class="font-semibold bg-contain text-9xl text-blue">
                    {{ level }}
                </header>
                <strong class="mt-1 text-2xl text-text">
                    Parabéns!
                </strong>
                <p>
                    Você subiu de nível!
                </p>
                <button
                    type="button"
                    class="absolute bg-transparent border-0 right-2 top-2"
                    @click="setModalState(false)"
                >
                    <img src="icons/close.svg" alt="Fechar Modal">
                </button>
            </div>
        </div>
    </transition>
</template>

<script lang="ts">

import Vue from 'vue'
import { mapState, mapMutations } from 'vuex';
import { Mutations } from '~/store/Challenges/types';

export default Vue.extend({
    computed: mapState('Challenges', ['level', 'isLevelUpModalOpen']),
    methods: mapMutations('Challenges', {
        setModalState: Mutations.SET_IS_LEVEL_UP_MODAL_OPEN,
    })
})
</script>

<style scoped>
    .overlay {
        background-color: rgba(242, 243, 245, 0.8);
    }

    header {
        background: url('/icons/levelup.svg') no-repeat center;
    }
    
    button {
        font-size: 0;
    }
</style>
