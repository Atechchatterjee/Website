<script lang="ts">
	import Block from './Block.svelte';

	let {
		focused = false,
		onClick = () => {},
		onFocus = () => {}
	} = $props<{
		focused: boolean;
		onClick: (_: any) => void;
		onFocus: (_: any) => void;
	}>();
</script>

<Block className="gap-9 pt-4 pb-7 text-lg text-[#535365]" {focused} {onClick} {onFocus}>
	<p class="text-lg font-medium text-white">Contact</p>
	<div class="flex flex-col gap-2">
		Reach out at
		<br />
		<span class="flex gap-2">
			Email: <br />
			<span class="text-white underline underline-offset-4">atechchatterjeee@gmail.com</span>
		</span>
		<span class="flex gap-2">
			Github:
			<a
				href="https://www.github.com/Atechchatterjee"
				class="text-white underline underline-offset-4">https://www.github.com/Atechchatterjee</a
			>
		</span>
	</div>
</Block>
