<script lang="ts">
	import Block from './Block.svelte';

	let selectedSection = $state(0);

	let {
		focused = false,
		onClick = () => {},
		onFocus = () => {}
	} = $props<{
		focused: boolean;
		onClick: (_: any) => void;
		onFocus: (_: any) => void;
	}>();

	function handleKeyDown(e: any) {
		if (!focused) return;
		if (e.key === 'j') {
			if (selectedSection < 3) selectedSection += 1;
		}
		if (e.key === 'k') {
			if (selectedSection > 0) selectedSection -= 1;
		}
		if (e.key === 'Enter') {
			//createBlock(sections[selectedSection]);
		}
	}
</script>

<Block className="gap-3 py-4 text-lg text-[#535365]" {focused} {onClick} {onFocus}>
	<p class="text-lg text-white">Projects</p>
	<div class="ml-8 flex flex-col gap-2">
		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => focused && (selectedSection = 0)}
			role="button"
			tabindex={0}
		>
			<p class={selectedSection === 0 ? 'font-bold text-white' : ''}>> Filezzy</p>
			<p>- (A cross-platform file manager built for efficiency)</p>
			{#if selectedSection === 0}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>

		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => focused && (selectedSection = 1)}
			role="button"
			tabindex={1}
		>
			<p class={selectedSection === 1 ? 'font-bold text-white' : ''}>> HotTakes App</p>
			<p>- (A community driven apps for your hottakes)</p>
			{#if selectedSection === 1}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>
	</div>
</Block>

<svelte:window on:keydown={handleKeyDown} />
