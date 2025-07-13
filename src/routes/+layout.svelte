<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<main class="mx-auto max-w-4xl">
	{@render children()}
</main>
