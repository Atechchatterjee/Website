<script lang="ts">
	import { twMerge } from 'tailwind-merge';
	export let className = '';
	export let focused = false;
	export let onClick = (_: any) => {};
</script>

<div
	class={twMerge(
		'flex min-h-[3.5rem] w-full flex-col justify-center border-b border-[#393946] px-10',
		focused ? 'border-l-4 border-l-white bg-[#14141D]' : '',
		className
	)}
	onclick={onClick}
	role="none"
>
	<slot />
</div>
