<template>
	<ul>
		<learning-resource
			v-for="storedResource in storedResources"
			:key="storedResource.id"
			:title="storedResource.title"
			:description="storedResource.description"
			:link="storedResource.link"
		/>
	</ul>
</template>

<script>
	import LearningResource from "./components/resources/LearningResource.vue";

	export default {
		components: {
			LearningResource,
		},
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
