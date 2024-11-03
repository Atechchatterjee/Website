<script lang="ts">
	import { twMerge } from 'tailwind-merge';
	let {
		className = '',
		id = '',
		onClick = () => {},
		onFocus = () => {},
		focused = false,
		children
	} = $props<{
		className?: string;
		id?: string;
		onClick: (_: any) => void;
		onFocus?: (_: any) => void;
		focused: boolean;
		children: any;
	}>();
</script>

<div
	{id}
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
