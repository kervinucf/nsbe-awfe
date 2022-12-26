<script lang="ts">
	import { onMount } from 'svelte';

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
			var days = Math.floor(distance / (1000 * 60 * 60 * 24)).toString();
			var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)).toString();
			var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60)).toString();
			var seconds = Math.floor((distance % (1000 * 60)) / 1000).toString();

			// Output the result in an element with class="value" id="demo"
			document.getElementById('days').innerHTML = days;
			document.getElementById('hours').innerHTML = hours;
			document.getElementById('minutes').innerHTML = minutes;
			document.getElementById('seconds').innerHTML = seconds;
			// If the count down is over, write some text
			if (distance < 0) {
				clearInterval(x);
				document.getElementById('demo').innerHTML = 'EXPIRED';
			}
		}, 1000);
	});
</script>

<div class="time">
	<div class="time-slot">
		<div class="value" id="days" />
		<div class="unit">Days</div>
	</div>
	<div class="time-slot">
		<div class="value" id="hours" />
		<div class="unit">Hours</div>
	</div>
	<div class="time-slot">
		<div class="value" id="minutes" />
		<div class="unit">Minutes</div>
	</div>
	<div class="time-slot">
		<div class="value" id="seconds" />
		<div class="unit">Seconds</div>
	</div>
</div>

<style>
	.time {
		display: flex;
		margin-left: auto;
		margin-right: auto;
		margin-top: 1rem;
		column-gap: 1.5rem;
		font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial,
			sans-serif;
	}
	.time-slot {
		display: grid;
		row-gap: 1rem;
	}
	.unit {
		font-size: xx-small;
	}
	.value {
		font-weight: 500;
		font-size: x-large;
	}
</style>
