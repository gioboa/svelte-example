<script lang="ts">
	import { Route, Router } from 'svelte-navigator';
	import About from './lib/About.svelte';
	import Contacts from './lib/Contacts.svelte';
	import Home from './lib/Home.svelte';
	import Navbar from './lib/Navbar.svelte';
</script>

<main>
	<Router primary={false}>
		<Navbar />

		<span>
			more component here - https://flowbite.com/docs/components/alerts/
		</span>

		<Route path="*">
			<Home />
		</Route>

		<Route path="/about">
			<About />
		</Route>

		<Route path="/contacts">
			<Contacts name={'My name'} />
		</Route>
	</Router>
</main>
