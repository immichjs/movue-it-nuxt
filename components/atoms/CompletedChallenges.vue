<template>
	<div class="flex items-center justify-between pb-5 mt-8 font-medium border-b-2 border-gray-line lg:mt-14">
		<p class="text-lg">
			Completed challenges
		</p>
		<p class="text-2xl">
			{{ completedChallenges }}
		</p>
	</div>
</template>

<script lang="ts">
import Vue from 'vue';
import { mapState } from 'vuex';

export default Vue.extend({
	computed: mapState('Challenges', ['completedChallenges']),
});
</script>
