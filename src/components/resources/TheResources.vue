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
	<keep-alive>
		<component :is="selectedTab"></component>
	</keep-alive>
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
				addResource: this.addResource,
				deleteResource: this.removeResource,
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
			addResource(title, description, link) {
				const newResource = {
					id: new Date().toISOString(),
					title: title,
					description: description,
					link: link,
				};
				this.storedResources.unshift(newResource);
				this.selectedTab = "stored-resource";
			},
			removeResource(resourceId) {
				const resourceIndex = this.storedResources.findIndex(
					(res) => res.id === resourceId
				);
				this.storedResources.splice(resourceIndex, 1);
			},
		},
	};
</script>
