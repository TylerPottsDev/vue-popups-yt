<template>
	<main>
		<h1>Vue Popups</h1>
		<button @click="() => TogglePopup('buttonTrigger')">Open Popup</button>
		
		<Popup 
			v-if="popupTriggers.buttonTrigger" 
			:TogglePopup="() => TogglePopup('buttonTrigger')">
			<h2>My Button Popup</h2>
		</Popup>
		<Popup 
			v-if="popupTriggers.timedTrigger"
			:TogglePopup="() => TogglePopup('timedTrigger')">
			<h2>My Timed Popup</h2>
			<p>
				Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis, accusantium sequi. Libero velit assumenda odio dolor repellendus earum debitis culpa voluptatum, illum beatae? Quasi, modi omnis repellat adipisci voluptate assumenda!
			</p>
		</Popup>
	</main>
</template>

<script>
import { ref } from 'vue';
import Popup from './components/Popup';

export default {
	setup () {
		const popupTriggers = ref({
			buttonTrigger: false,
			timedTrigger: false
		});

		const TogglePopup = (trigger) => {
			popupTriggers.value[trigger] = !popupTriggers.value[trigger]
		}

		setTimeout(() => {
			popupTriggers.value.timedTrigger = true;
		}, 3000);

		return {
			Popup,
			popupTriggers,
			TogglePopup
		}
	}
}
</script>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
