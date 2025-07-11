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
			style: { fontSize: '2em', display: 'inline-block' },
			repeat: Infinity
		});
	};

	function Counter() {
		const [count, setCount] = useState(0);
		return createElement(
			'div',
			null,
			createElement('h1', null, 'Counter'),
			createElement('p', null, `Count: ${count}`),
			createElement('button', { onClick: () => setCount(count + 1) }, 'Increment')
		);
	}

	let rootEl: HTMLElement;

	$effect(() => {
		const root = createRoot(rootEl);

		const welcome = createElement('p', { className: 'welcome' }, 'Welcome to Excalidraw');

		root.render(
			createElement(
				StrictMode,
				null,
				welcome,
				createElement(Counter, null),
				createElement(ExampleComponent, null)
			)
		);

		return () => root.unmount();
	});
</script>

<div bind:this={rootEl} class="root"></div>
