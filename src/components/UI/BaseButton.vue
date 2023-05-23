<template>
	<button :type="type" :class="mode">
		<slot></slot>
	</button>
</template>

<script>
	export default {
		props: ["type", "mode"],
	};
</script>

<style scoped>
	button {
		padding: 0.75rem 1.5rem;
		font-family: inherit;
		background-color: #006434;
		border: 1px solid #006434;
		color: white;
		cursor: pointer;
	}

	button:hover,
	button:active {
		background-color: #004119;
		border-color: #004119;
	}

	.flat {
		background-color: transparent;
		color: #004119;
		border: none;
	}

	.flat:hover,
	.flat:active {
		background-color: #bbffacc5;
	}
</style>
