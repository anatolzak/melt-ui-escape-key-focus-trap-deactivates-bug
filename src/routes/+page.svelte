<script lang="ts">
	import { createDialog, melt } from '@melt-ui/svelte';

	const {
		elements: { trigger, overlay, content, title, portalled },
		states: { open }
	} = createDialog({ forceVisible: true, closeOnEscape: false });
</script>

<button
	use:melt={$trigger}
	class="inline-flex items-center justify-center rounded-md bg-gray-950 px-4 py-2 font-medium leading-none text-blue-700 shadow-lg focus-within:border-4 focus-within:border-red-500 focus-within:shadow-blue-400 focus-within:outline-none hover:opacity-75"
>
	Open Dialog
</button>
{#if $open}
	<div class="" use:melt={$portalled}>
		<div use:melt={$overlay} class="fixed inset-0 z-50 bg-black/50" />
		<div
			class="fixed left-[50%] top-[50%] z-50 max-h-[85vh] w-[90vw]
            max-w-[450px] translate-x-[-50%] translate-y-[-50%] rounded-md bg-gray-950
            p-6 shadow-lg"
			use:melt={$content}
		>
			<h2 use:melt={$title} class="m-0 text-lg font-medium text-white">First dialog</h2>
			<button
				class="text-white focus-within:border-4 focus-within:border-red-500 focus-within:shadow-blue-400 focus-within:outline-none"
				>some button</button
			>
			<button
				class="text-white focus-within:border-4 focus-within:border-red-500 focus-within:shadow-blue-400 focus-within:outline-none"
				>some button</button
			>
		</div>
	</div>
{/if}
