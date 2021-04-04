<template>
	<div class="flex flex-col max-w-5xl min-h-screen px-5 py-8 mx-auto md:py-10">
		<ExperienceBar />
		<Nuxt />
	</div>
</template>

<script lang="ts">
import Vue from 'vue';
import ExperienceBar from '~/components/atoms/ExperienceBar.vue';

export default Vue.extend({
	name: 'Default',
	components: {
		ExperienceBar,
	},
});
</script>
