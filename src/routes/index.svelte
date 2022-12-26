<script lang="ts">
	import Resources from '../pages/Resources.svelte';
	import Landing from '../pages/Landing.svelte';
	import Navigation from '../components/Navigation.svelte';
	import { onMount } from 'svelte';

	let days = null;
	let hours = null;
	let event_started = false;

	onMount(() => {
		// Set the date we're counting down to
		var countDownDate = new Date('Feb 26, 2022 09:00:00').getTime();

		// Update the count down every 1 second
		var x = setInterval(function () {
			// Get today's date and time
			var now = new Date().getTime();

			// Find the distance between now and the count down date
			var distance = countDownDate - now;

			// Time calculations for days, hours, minutes and seconds
			days = Math.floor(distance / (1000 * 60 * 60 * 24)).toString();
			hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)).toString();

			// Output the result in an element with class="value" id="demo"
			// If the count down is over, write some text
			if (distance < 0) {
				clearInterval(x);
				event_started = true;
			}
		}, 100);
	});
</script>

<div class="home" id="home">
	<div class="navigation-container"><Navigation /></div>
	<div class="landing-container"><Landing /></div>
	{#if event_started || (days == 0 && hours < 5)}
		<div class="resources-container"><Resources /></div>
	{/if}
</div>

<style>
	.home {
		display: grid;
	}
	/* Medium devices (landscape tablets, 768px and up) */
	@media only screen and (min-width: 768px) {
		.navigation-container {
			display: none;
		}
	}
</style>
