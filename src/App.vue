<template>
	<img alt="Vue logo" src="./assets/logo.png" />
	<HelloWorld msg="Welcome to Your Vue.js App" />
	<teleport to=".modal">
		<Modal
			v-if="show_modal"
			:title="title"
			subtitle="Test Subtitle"
			v-bind:button_text="button_text"
			theme="dark"
			@close_modal="toggle_modal"
		>
			<h1>Passed template with slot</h1>
			<template v-slot:content>
				<h2>Passed from named slot</h2>
			</template>
		</Modal>
	</teleport>
	<h2>{{ title }}</h2>
	<button @click="toggle_modal">Show Modal</button>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Modal from "./components/Modal.vue";

export default {
	name: "App",
	components: {
		HelloWorld,
		Modal,
	},
	data() {
		return { title: "Test Title", button_text: "Button Text", show_modal: false };
	},
	methods: {
		toggle_modal() {
			this.show_modal = !this.show_modal;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
