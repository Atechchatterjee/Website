<script lang="ts">
	import { twMerge } from 'tailwind-merge';
	//export let focused = $state(false);
	//export let className = '';
	//export let onClick = (_: any) => {};
	//export let onFocus = (_: any) => {};
	let {
		className = '',
		onClick = () => {},
		onFocus = () => {},
		focused = false,
		children
	} = $props<{
		className: string;
		onClick: (_: any) => void;
		onFocus: (_: any) => void;
		focused: boolean;
		children: any;
	}>();
</script>

<div
	class={twMerge(
		'flex min-h-[3.5rem] w-full flex-col justify-center border-b border-[#393946] px-10',
		focused ? 'border-l-4 border-l-white bg-[#14141D]' : '',
		className
	)}
	onclick={onClick}
	onfocus={onFocus}
	role="none"
>
	{@render children()}
</div>
