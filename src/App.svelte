<script>
	let firstName = 'Jimi';
	let lastName = 'Hendrix';
	let beltColour = 'black';

	$: fullname = `${firstName} ${lastName}`;
	$: {
		console.log(beltColour);
		console.log(fullname);
	}

	const handleClick = () => {
		beltColour = 'Orange'
	}

	const handleInput = (e) => {
		beltColour = e.target.value
	}

	// Loops
	let people = [
		{ name: 'Yoshi', colorOfBelt: 'Black', age: 25, id: 1 },
		{ name: 'Mario', colorOfBelt: 'Orange', age: 45, id: 2 },
		{ name: 'Luigi', colorOfBelt: 'Brown', age: 35, id: 3 },
	];


	const deleteButton = (id) => {
		// Delete the person from people
		people = people.filter((person) => person.id != id)
	}
</script>

<main>
	<p>{fullname} - {beltColour} belt</p>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltColour}>

	<h1>Learning LOOPS!</h1>
	<p>Section for practicing about loops<br/>
	button for learning about inlinve event handlers </p>

	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.age} years old, {person.colorOfBelt} belt.</p>
			<button on:click={() => deleteButton(person.id)}>Delete</button>
		</div>
	<!-- Else buat misalkan engga ada element di dalam array -->
	{:else}
		<p>There are no people to show</p>
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
		font-size: 3em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>