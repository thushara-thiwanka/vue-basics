<template>
	<div class="backdrop" v-on:click.self="close_modal">
		<div class="content" v-bind:class="{ dark: theme === 'dark' }">
			<slot></slot>
			<slot name="content"></slot>
			<h1 class="title">{{ title }}</h1>
			<h2>{{ subtitle }}</h2>
			<button>{{ button_text }}</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "ModalComponent",
	props: ["title", "subtitle", "button_text", "theme"],
	methods: {
		close_modal() {
			this.$emit("close_modal");
		},
	},
};
</script>

<style scoped>
.backdrop {
	width: 100%;
	height: 100%;
	position: fixed;
	top: 0;
	left: 0;
	background-color: rgba(0, 0, 0, 0.25);
	display: grid;
	place-items: center;
}
.content {
	width: 300px;
	height: 200px;
	background-color: white;
	padding: 2rem;
}
.content.dark {
	background-color: darkslategrey;
	color: white;
}
</style>
