<script lang="ts">
	export let title;
	export let flyers;

	let openFile = (pdf: string) => {
		if (pdf == 'number8') {
			window.open(`./pdfs/${pdf}.png`);
		} else {
			window.open(`./pdfs/${pdf}.pdf`);
		}
	};
</script>

<div class="resource" id={title}>
	<h3>{title}</h3>
	<div class="flyers">
		{#each flyers as flyer}
			<div class="flyer" on:click={() => openFile(flyer)}>
				<img alt="" src={`./pngs/${flyer}.png`} />
			</div>
		{/each}
	</div>
</div>

<style>
	img {
		width: 100%;
		max-width: 700px;
	}
	.resource {
		margin-left: 1rem;
		margin-right: 1rem;
		display: grid;
		row-gap: 1rem;
	}
	.flyers {
		display: grid;
		row-gap: 2rem;
	}
	.flyer {
		cursor: pointer;
	}
	.flyer img:hover {
		box-shadow: 0 2px 15px 12px #0000003b;
	}
	/* Medium devices (landscape tablets, 768px and up) */
	@media only screen and (min-width: 768px) {
		.flyers {
			row-gap: 7rem;
		}
		img {
			width: 100%;
			max-width: 600px;
			height: 100%;
		}
		h3 {
			font-size: 2rem;
		}
	}
</style>
