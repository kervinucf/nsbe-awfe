<script lang="ts">
	let menuClicked = false;

	let clickMenu = () => {
		menuClicked = !menuClicked;
	};
	let scrollTo = (id: string) => {
		menuClicked = false;
		document.getElementById(id).scrollIntoView();
	};

	let links = ['All Things NSBE', 'College Preparation', 'Financial Aid', 'More Resources'];
</script>

<div class="nav-bar">
	<div class="content">
		<div class="home"><div class="home-text">AWFE 2022</div></div>
		<div>
			<i id="menu" class="fa fa-bars menu" on:click={() => clickMenu()} />
		</div>
	</div>
	{#if menuClicked}
		<div class="options">
			<div class="bg">
				<div class="links">
					{#each links as link}
						<div on:click={() => scrollTo(link)}>
							{link}
						</div>
					{/each}
				</div>
			</div>
		</div>
	{/if}
</div>

<style>
	.nav-bar {
		background-color: #242424e5;
		height: 50px;
		box-shadow: 0 2px 5px 2px #0000003b;
		width: 100% !important;
		display: grid;
		color: white;
	}
	.content {
		display: grid;
		grid-template-columns: 10fr 1fr;
		font-size: larger;
		text-align: center;
		margin-top: auto;
		margin-bottom: auto;
	}

	.home-text {
		float: left;
		margin-left: 1rem;
	}
	.options {
		display: flex;
		background-color: red;
	}
	.bg {
		background-color: #cde2d7;
		width: 100%;
		position: absolute;
		color: black;
		font-weight: 500;
	}
	.links {
		margin-left: auto;
		width: 100%;
		text-align: center;
		display: grid;
		row-gap: 4rem;
		font-size: larger;
		margin-top: 1.5rem;
		margin-bottom: 1.5rem;
	}
</style>
