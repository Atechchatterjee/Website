<script lang="ts">
	import Block from './Block.svelte';

	let selectedSection = $state(0);
	type createBlockType = 'project' | 'experience' | 'tech' | 'contact';
	let {
		focused = false,
		onClick = () => {},
		createBlock = () => {}
	} = $props<{
		focused: boolean;
		onClick: (_: any) => void;
		createBlock: (_: createBlockType) => void;
	}>();

	const sections = ['project', 'experience', 'tech', 'contact'];

	function handleKeyDown(e: any) {
		if (!focused) return;
		if (e.key === 'j') {
			if (selectedSection < 3) selectedSection += 1;
		}
		if (e.key === 'k') {
			if (selectedSection > 0) selectedSection -= 1;
		}
		if (e.key === 'Enter') {
			createBlock(sections[selectedSection]);
		}
	}
</script>

<Block className="gap-3 py-4 text-lg text-[#535365]" {focused} {onClick}>
	<p class="text-white">Sections:</p>
	<div class="ml-8 flex flex-col gap-2">
		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => (selectedSection = 0)}
			role="button"
			tabindex={0}
		>
			<p class={selectedSection === 0 ? 'font-bold text-white' : ''}>> Projects</p>
			{#if selectedSection === 0}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>

		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => (selectedSection = 1)}
			role="button"
			tabindex={1}
		>
			<p class={selectedSection === 1 ? 'font-bold text-white' : ''}>> Experience</p>
			{#if selectedSection === 1}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>

		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => (selectedSection = 2)}
			role="button"
			tabindex={2}
		>
			<p class={selectedSection === 2 ? 'font-bold text-white' : ''}>> Tech</p>
			{#if selectedSection === 2}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>

		<div
			class="flex w-fit cursor-pointer gap-5"
			onmousemove={() => (selectedSection = 3)}
			role="button"
			tabindex={3}
		>
			<p class={selectedSection === 3 ? 'font-bold text-white' : ''}>> Contact</p>
			{#if selectedSection === 3}
				<p class="italic text-[#535365]">Enter ⏎</p>
			{/if}
		</div>
	</div>
</Block>

<svelte:window on:keydown={handleKeyDown} />
