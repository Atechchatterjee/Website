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

<Block className="gap-3 py-4 text-lg text-[#535365]" {focused} {onClick} {onFocus}>
	<p class="text-lg font-medium text-white">Experience</p>
	<div class="ml-8 flex flex-col gap-2">
		<p class="italic text-white">Software Engineer Intern</p>
		<p>
			During a 12-week Software Engineering Internship at CND Engineering Pvt Ltd, I contributed to
			enhancing an e-commerce platform by developing features for the dashboard, project management,
			and product management modules. My work included implementing user, product, sales, and
			revenue metrics, creating tools for managing projects, and optimizing product management for
			seamless inventory control. This role provided valuable hands-on experience in full-stack
			development and strengthened my technical and problem-solving skills.
		</p>
	</div>
</Block>
