<script lang="ts">
	import { io } from 'socket.io-client';

	import { onMount } from 'svelte';
	let name;
	let color;
	let student = null;
	onMount(() => {
		connect_websocket();
	});

	const emit_events = (socket) => {
		socket.emit('get-color');
	};

	let connect_websocket = async function () {
		var socket = io('https://api.kervinsilaire.com:443', { forceNew: true });
		socket.on('connect', async () => {
			socket.emit('register', socket.id);
			emit_events(socket);
		});

		socket.on('color-change', async (data) => {
			console.log(data);
			document.getElementById('demo').style.backgroundColor = data['color'];
			student = data['student'];
		});
	};
	const isColor = (strColor) => {
		const s = new Option().style;
		s.color = strColor;
		return s.color !== '';
	};
	let make_new_bg = (reset = false) => {
		if (reset) {
			fetch(`https://api.kervinsilaire.com/nsbe_set/Kervin/green`, {
				credentials: 'same-origin'
			});
		} else {
			if (name && isColor(color)) {
				fetch(`https://api.kervinsilaire.com/nsbe_set/${name}/${color}`, {
					credentials: 'same-origin'
				});
			} else {
				error = true;
			}
		}
	};
	let error = false;
</script>

<div style="text-align:center;height:100vh;" id="demo">
	<div style="font-weight: bold;font-size:3rem;padding:4rem">NFC TAG DEMO</div>
	{#if error}
		<div>Please enter a name or a valid color</div>
	{/if}
	{#if student}
		<div style="font-size: 2rem">
			This color was chosen by: {student}
		</div>
	{/if}

	<div
		style="max-width:700px;display:grid; width:80%;margin-left:auto;margin-right:auto;margin-top:3rem;row-gap:1.5rem"
	>
		<input type="text" placeholder="&nbsp; Name" bind:value={name} />
		<input type="text" placeholder="&nbsp; Color" bind:value={color} />
		<div
			style="display:grid;row-gap:3rem;margin-top: 1rem;width:70%;;margin-left:auto;margin-right:auto;"
		>
			<div class="btn">
				<a href="#" on:click={() => make_new_bg()}>Submit</a>
			</div>
			<div class="btn">
				<a href="#" on:click={() => make_new_bg(true)}>Reset</a>
			</div>
		</div>
	</div>
</div>

<style>
	input {
		height: 40px;
		border-radius: 0.25rem;
		font-size: 17px;
	}
	.btn {
		background-color: rgb(255, 255, 255);
		height: 45px;
		border-radius: 0.25rem;
		color: rgb(0, 0, 0);
		display: grid;
		border: 2px solid black;
	}
	a {
		margin: auto;
		font-size: larger;
		text-decoration: none;
	}
</style>
