<script lang="ts">
	import { createElement, StrictMode, useState } from 'react';
	import { createRoot } from 'react-dom/client';
	import { TypeAnimation } from 'react-type-animation';

	const ExampleComponent = () => {
		return createElement(TypeAnimation, {
			sequence: [
				'We produce food for Mice',
				1000,
				'We produce food for Hamsters',
				1000,
				'We produce food for Guinea Pigs',
				1000,
				'We produce food for Chinchillas',
				1000
			],
			wrapper: 'span',
			speed: 50,
			style: {
				fontSize: '2em',
				display: 'inline-block',
				fontWeight: 'bold',
				color: '#2cbb3f',
				paddingTop: '18px'
			},
			repeat: Infinity
		});
	};

	function Counter() {
		const [count, setCount] = useState(0);
		return createElement(
			'div',
			{
				className: 'counter'
			},
			createElement('h1', null, 'Counter'),
			createElement('p', null, `Count: ${count}`),
			createElement('button', { onClick: () => setCount(count + 1), className: 'btn' }, 'Increment')
		);
	}

	let rootEl: HTMLElement;

	$effect(() => {
		const root = createRoot(rootEl);

		root.render(
			createElement(
				StrictMode,
				null,
				createElement(Counter, null),
				createElement(ExampleComponent, null)
			)
		);

		return () => root.unmount();
	});
</script>

<div class="my-10 flex flex-col gap-10">
	<p class="welcome">Welcome to React with Svelte</p>
	<p>
		↓↓↓↓↓ this code client side with svelte and typing effect with react library
		npm:react-type-animation ↓↓↓↓↓
	</p>
	<div bind:this={rootEl}></div>
</div>
