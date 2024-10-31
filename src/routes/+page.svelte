<script lang="ts">
	import Navbar from '../components/Navbar.svelte';
	import SideIllustration from '$lib/assets/side-illustration.svg';
	import Block from '../components/Block.svelte';
	import SectionBlock from '../components/Section-Block.svelte';

	let maxBlocks = 3;

	let focusedBlock = $state(2);
	let pressedShift = $state(false);

	let additionalBlocks = $state([]);

	function handleKeyUp(e: any) {
		if (e.key === 'Shift') pressedShift = false;
	}

	function handleKeyDown(e: any) {
		if (e.key === 'Tab') {
			e.preventDefault();
			if (pressedShift) focusedBlock -= focusedBlock > 0 ? 1 : 0;
			else focusedBlock += focusedBlock < maxBlocks - 1 ? 1 : 0;
		}
		if (e.key === 'Shift') pressedShift = true;
	}
</script>

<div class="flex h-[100vh] w-full">
	<div class="flex>1">
		<img src={SideIllustration} alt="logo" class="h-[100vh] object-cover" />
	</div>

	<div class="w-[72%] border border-[#393946] bg-[#0A0A0E]">
		<Navbar />
		<Block focused={focusedBlock === 0} onClick={() => (focusedBlock = 0)}>
			<p class="text-lg text-[#535365]">1. # Hey This is Anish Chattopadhyay</p>
		</Block>
		<Block focused={focusedBlock === 1} onClick={() => (focusedBlock = 1)}>
			<p class="text-lg text-[#535365]">2. # Welcome To My Website</p>
		</Block>
		<SectionBlock
			focused={focusedBlock === 2}
			onClick={() => {
				focusedBlock = 2;
			}}
			createBlock={(blockType) => {
				alert(blockType);
			}}
		/>
		{#each additionalBlocks as block}
			<Block>
				{block}
			</Block>
		{/each}
	</div>
	<div class="flex-1">
		<img src={SideIllustration} alt="logo" class="h-[100vh] object-cover" />
	</div>
</div>

<svelte:window on:keydown={handleKeyDown} on:keyup={handleKeyUp} />
