<script lang="ts">
	let open_link = (url: string, same = false) => {
		if (same) {
			window.open(url, '_self');
		} else {
			window.open(url);
		}
	};
</script>

<div class="landing">
	<div class="content">
		<div class="nsbe-info">
			<div class="logo">
				<img alt="" src="./logo.png" />
			</div>
			<div class="nsbe-header">National Society of <br />Black Engineers UCF Chapter</div>
			<h4 class="nsbe-statement statement">
				Our mission is <span class="quote"
					>“to increase the number of culturally responsible black engineers who excel academically,
					succeed professionally and positively impact the community."</span
				>
			</h4>
		</div>
		<div class="nsbe-event">
			<h2 class="event-header">A Walk for Education</h2>
			<div class="event-start">
				<div class="event-date">Saturday Februrary 26th, 2022</div>
				<div class="event-time">9:00 AM - 3:00 PM</div>
			</div>
			<h4 class="event-statement statement">
				Our goal is <span class="quote"
					>“to increase awareness of opportunities available through education in the STEM fields
					and to change the narrative about African-Americans in math, science, engineering and
					other technologies.”</span
				>
			</h4>
			<div class="sign-ups">
				<div class="btns">
					<div
						class="btn"
						on:click={() => {
							open_link('https://rb.gy/d4ffol');
						}}
					>
						<a>Parent/Student Sign Up</a>
					</div>
					<div
						class="btn"
						on:click={() => {
							open_link(
								'https://docs.google.com/forms/d/e/1FAIpQLSeWK4n-NOnEKHqpVJ_vghBsf-Rgj0p_lCnJkaeJG1nBxLbSow/viewform'
							);
						}}
					>
						<a>Volunteer Sign Up</a>
					</div>
					<div
						class="btn-demo"
						on:click={() => {
							open_link('/demo', true);
						}}
					>
						<a>NFC TAG DEMO</a>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

<style>
	.event-header {
		margin-top: -0.25rem;
	}
	.sign-ups {
		margin-top: 1rem;
	}
	.btns {
		display: grid;
		row-gap: 1.5rem;
		width: 80%;
		margin: auto;
	}
	.btn {
		cursor: pointer;
		background-color: rgb(18, 126, 85);
		height: 50px;
		border-radius: 0.35rem;
		display: grid;
		font-size: 1.25rem;
		font-weight: 500;
		box-shadow: 0 0 10px 4px rgba(20, 20, 20, 0.164);
		color: white;
	}
	.btn-demo {
		cursor: pointer;
		background-color: rgb(18, 56, 126);
		height: 50px;
		border-radius: 0.35rem;
		display: grid;
		font-size: 1.25rem;
		font-weight: 500;
		box-shadow: 0 0 10px 4px rgba(20, 20, 20, 0.164);
		color: white;
	}
	.btn a {
		margin: auto;
		text-decoration: none;
		color: white;
	}
	.btn-demo a {
		margin: auto;
		text-decoration: none;
		color: white;
	}
	.statement {
		color: rgba(3, 0, 88, 0.597);
		margin-left: 2.5em;
		margin-right: 2.5rem;
		font-size: 0.85rem;
		line-height: 1.75rem;
		font-weight: 400;
	}
	.quote {
		font-style: italic;
	}
	img {
		width: 100px;
	}
	.landing {
		height: 100vh;
	}
	.content {
		text-align: center;

		width: 100%;
	}
	h4 {
		font-weight: 200;
		font-size: large;
		line-height: 1.5rem;
	}

	.event-start {
		display: grid;
		font-weight: 400;
		row-gap: 1rem;
	}
	.nsbe-info {
		display: grid;
		margin-top: 2.25rem;
		row-gap: 0.5rem;
	}
	.nsbe-event {
		display: grid;
		font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial,
			sans-serif;
	}
	/* Medium devices (landscape tablets, 768px and up) */
	@media only screen and (min-width: 768px) {
		.statement {
			line-height: 3rem;
		}
		.landing {
			display: flex;
		}
		img {
			width: 200px;
		}
		.nsbe-header {
			font-size: x-large;
			font-weight: 500;
		}
		.content {
			display: flex;
			column-gap: 4rem;
		}
		.nsbe-info {
			margin-left: 5rem;
			margin-right: 5rem;
		}
		.nsbe-event {
			margin-left: 5rem;
			margin-right: 5rem;
			margin-bottom: auto;
			margin-top: auto;
		}
		.nsbe-header {
			line-height: 3rem;
		}
		.btns {
			display: grid;
			row-gap: 3rem;
		}
	}
</style>
