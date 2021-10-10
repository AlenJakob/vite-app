<template>
	<div class="card-wrapper">
		<div class="card">
			<div class="card-image">
				<figure class="image is-4by3">
					<img
						src="https://bulma.io/images/placeholders/1280x960.png"
						alt="Placeholder image"
					/>
				</figure>
			</div>
			<div class="card-content">
				<div class="media">
					<div class="media-left">
						<figure class="image is-48x48">
							<img
								src="https://bulma.io/images/placeholders/96x96.png"
								alt="Placeholder image"
							/>
						</figure>
					</div>
					<div class="media-content">
						<p class="title is-4">{{ movie.title }}</p>
						<p class="subtitle is-6">@johnsmith</p>
					</div>
				</div>

				<div class="content">
					Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec
					iaculis mauris. <a>@bulmaio</a>. <a href="#">#css</a>
					<a href="#">#responsive</a>
					<br />
					<time datetime="2016-1-1">{{ convertDate(movie.release) }}</time>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
import { computed } from "vue"
import { convertDate } from "../../services/helpers"
const props = defineProps({
	movie: Object,
	default: () => ({}),
})
const movie = computed(() => {
	return props.movie
})
</script>

<style  scoped>
.card-wrapper {
	width: 300px;
	margin: 1rem;
}
</style>