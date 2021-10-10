<template>
	<div class="columns is-multiline is-3-desktop is-8-widescreen is-2-fullhd">
		<the-card v-for="movie in movies" :key="movie" :movie="movie"></the-card>
	</div>
</template>

<script setup>
import TheCard from "./TheCard.vue"
import { defineProps, toRefs, computed } from "vue"

const props = defineProps({
	moviesUpcoming: {
		type: Array,
		default: () => [],
	},
})

 const movies = computed(() => {
	return moviesUpcoming.value['Movies Upcoming']
})


const { moviesUpcoming } = toRefs(props)
</script>

<style>
</style>