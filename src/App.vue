

<template>
	<div class="">
		<h1>welcome</h1>
		<button @click.once="fetchMovies()">load Movies</button>
		<input v-model="searchedMovie" type="text" />
		<card-wrapper :moviesUpcoming="moviesUpcoming"></card-wrapper>
	</div>
</template>

<style>
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.0/css/bulma.min.css";
</style>

<script setup>
import axios from "axios"
import { ref } from "vue"
import CardWrapper from "./components/CardWrapper.vue"
const apiKey = "5cf140129dmsh4ef83c7830eaa78p131ca2jsnbd89ce55eac8"

let moviesUpcoming = ref([])
const fetchMovies = async (type = "order", value = "upcoming") => {
	try {
		const movies = await axios.get(
			`https://data-imdb1.p.rapidapi.com/movie/${type}/${value}/`,
			{
				headers: {
					"x-rapidapi-host": "data-imdb1.p.rapidapi.com",
					"x-rapidapi-key": apiKey,
				},
			}
		)
		moviesUpcoming.value = movies.data
	} catch (err) {
		console.log(new Error("Movie not found", err))
	}
}

const fetchMoviesById = async (imdbId = "tt6856242") => {
	try {
		console.log("TEST", moviesUpcoming.value)
		const moviesById = await axios.get(
			`https://data-imdb1.p.rapidapi.com/movie/id/${imdbId}/`,
			{
				headers: {
					"x-rapidapi-host": "data-imdb1.p.rapidapi.com",
					"x-rapidapi-key": apiKey,
				},
			}
		)
		console.log(moviesById)
	} catch (err) {
		console.log(new Error("Movie not found", err))
	}
}
</script>