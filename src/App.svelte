<script>
	let firstName = 'Brad';
	let lastName = 'Traversy';
	let color = 'blue';
	let showText = false;

	let users = [
		{
			id: 1,
			name: 'Putu'
		},
		{
			id: 2,
			name: 'Kadek'
		},
		{
			id: 3,
			name: 'Komang'
		}				
	]

	$: name = firstName + " " + lastName;	
	const toggle = () => {
		color = color === 'blue' ? 'red' : 'blue';
		showText = !showText;
		users = [...users, {id: 4, name: 'Ketut'}]
	}
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
	<p>No text</p>
	{/if}
	<button on:click={toggle}>Click</button>

	{#each users as user}
		<h3>{user.id}: {user.name}</h3>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>