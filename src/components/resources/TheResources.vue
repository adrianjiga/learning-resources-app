<template>
	<base-card>
		<base-button
			@click="setSelectedTab('stored-resource')"
			:mode="storedResBtnMode"
			>Stored Resources</base-button
		>
		<base-button @click="setSelectedTab('add-resource')" :mode="addResBtnMode"
			>Add Resources</base-button
		>
	</base-card>
	<component :is="selectedTab"></component>
</template>

<script>
	import StoredResource from "./StoredResource.vue";
	import AddResource from "./AddResource.vue";

	export default {
		components: {
			StoredResource,
			AddResource,
		},
		data() {
			return {
				selectedTab: "stored-resources",
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
		provide() {
			return {
				resources: this.storedResources,
			};
		},
		computed: {
			storedResBtnMode() {
				return this.selectedTab === "stored-resource" ? null : "flat";
			},
			addResBtnMode() {
				return this.selectedTab === "add-resource" ? null : "flat";
			},
		},
		methods: {
			setSelectedTab(tab) {
				this.selectedTab = tab;
			},
		},
	};
</script>
