<template>
	<ul v-for="storedResource in storedResources" :key="storedResource">
		<li>
			<h2>{{ storedResource.title }}</h2>
			<h3>{{ storedResource.description }}</h3>
			<h3>{{ storedResource.link }}</h3>
		</li>
	</ul>
</template>

<script>
	export default {
		data() {
			return {
				storedResources: [
					{
						id: "official-guide",
						title: "Official Guide",
						description: "The official Vue.js documentation",
						link: "https://vuejs.org",
					},
					{
						id: "google",
						title: "Google",
						description: "Learn to google...",
						link: "https://google.com",
					},
				],
			};
		},
	};
</script>
