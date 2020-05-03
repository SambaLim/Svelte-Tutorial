<script>
	let people = [
		{ name: 'Samba', beltColor: 'black', age:29, id:1 },
		{ name: 'Sound', beltColor: 'blue', age:25, id:2 },
		{ name: 'Mongo', beltColor: 'green', age:20, id:3 }
	];

	const handleClick = (id) => {
		people = people.filter((person) => {
			return person.id != id;
		});
	}

	let number = 5;

</script>

{#if number > 20}
	<p>Greater than 20</p>
{:else if number > 5}
	<p>Greater than 5</p>
{:else}
	<p>Not greater than 5</p>
{/if}

<main>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColor === 'black'}
				<p><strong>BLACK COLOR</strong></p>
			{/if}
			<p style="color: {person.beltColor}">{person.age} years old, {person.beltColor} belt.</p>
			<button on:click={() => handleClick(person.id)}>delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
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