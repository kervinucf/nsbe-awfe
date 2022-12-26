<script lang="ts">
	import Resource from '../components/Resource.svelte';
	let all_things_nsbe = {
		title: 'All Things NSBE',
		flyers: ['number5', 'number6', 'number7']
	};
	let college_prep = {
		title: 'College Preparation',
		flyers: ['number3', 'number1', 'number4']
	};
	let financial_aid = {
		title: 'Financial Aid',
		flyers: ['number2']
	};
	let others = {
		title: 'More Resources',
		flyers: ['number8', 'number9']
	};
</script>

<div class="resources">
	<h2>EVENT RESOURCES</h2>
	<Resource title={all_things_nsbe.title} flyers={all_things_nsbe.flyers} />
	<Resource title={college_prep.title} flyers={college_prep.flyers} />
	<Resource title={financial_aid.title} flyers={financial_aid.flyers} />
	<Resource title={others.title} flyers={others.flyers} />
</div>

<style>
	.resources {
		text-align: center;
		display: grid;
		row-gap: 2rem;
	}
	@media only screen and (min-width: 768px) {
		.resources {
			text-align: center;
			display: grid;
			row-gap: 10rem;
		}
		h2 {
			font-size: 3rem;
		}
	}
</style>
