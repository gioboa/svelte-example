<script lang="ts">
	import type { People } from 'src/types/types';
	import { getRandomNumber } from '../shared/common';

	const getRandomUser = async (): Promise<People> => {
		const res = await fetch(
			`https://swapi.dev/api/people/${getRandomNumber(1, 5)}`,
			{
				method: 'GET',
			}
		);

		console.log('response', res);
		if (res.ok) {
			return await res.json();
		} else {
			throw new Error('error');
		}
	};

	let httpCall = getRandomUser();

	const handleClick = () => {
		httpCall = getRandomUser();
	};
</script>

<br /><br />
<button type="button" class="button" on:click={handleClick}> GET </button>
<br /><br />

{#await httpCall}
	<p>...waiting</p>
{:then data}
	<p><br /><br />Name {data.name} <br /><br /> {JSON.stringify(data)}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
