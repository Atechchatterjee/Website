<script lang="ts">
	import Navbar from '../components/Navbar.svelte';
	import SideIllustration from '$lib/assets/side-illustration.svg';
	import Block from '../components/Block.svelte';
	import SectionBlock from '../components/Section-Block.svelte';
	import ProjectBlock from '../components/Project-Block.svelte';
	import ExperienceBlock from '../components/Experience-Block.svelte';
	import TechBlock from '../components/Tech-Block.svelte';
	import ContactBlock from '../components/Contact-Block.svelte';
	import { onMount } from 'svelte';

	let maxBlocks = 3;

	let focusedBlock = $state(2);
	let pressedShift = $state(false);

	let additionalBlocks: any[] = $state([]);

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

	let focusedBlockRef: any;

	function scrollIntoView(e: any) {
		//const el = document.querySelector(target);
		//if (!el) return;
		if (!e.target) return;
		e.target.scrollIntoView({
			behavior: 'instant',
			block: 'center',
			inline: 'nearest'
		});
	}
</script>

<div class="flex h-[100vh] w-full">
	<div class="flex-1">
		<img src={SideIllustration} alt="logo" class="h-[100vh] object-cover" />
	</div>

	<div class="h-[100vh] w-[72%] overflow-y-auto border border-[#393946] bg-[#0A0A0E]">
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
				if (blockType === 'project') {
					additionalBlocks.push(ProjectBlock);
				} else if (blockType === 'experience') {
					additionalBlocks.push(ExperienceBlock);
				} else if (blockType === 'tech') {
					additionalBlocks.push(TechBlock);
				} else if (blockType === 'contact') {
					additionalBlocks.push(ContactBlock);
				}
				maxBlocks += 1;
				focusedBlock = maxBlocks - 1;
				focusedBlockRef = additionalBlocks[focusedBlock];
			}}
		/>
		{#each additionalBlocks as ABlock, index}
			<ABlock
				focused={focusedBlock === index + 3}
				onFocus={(e: any) => {
					alert('focused');
					scrollIntoView(e);
				}}
				onClick={(e: any) => {
					scrollIntoView(e);
					focusedBlock = index + 3;
				}}
			/>
		{/each}
	</div>
	<div class="flex-1">
		<img src={SideIllustration} alt="logo" class="h-[100vh] object-cover" />
	</div>
</div>

<svelte:window on:keydown={handleKeyDown} on:keyup={handleKeyUp} />
