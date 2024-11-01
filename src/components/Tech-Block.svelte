<script lang="ts">
	import Block from './Block.svelte';
	import nextIcon from '../lib/assets/nextjs-icon.svg';
	import nodejsIcon from '../lib/assets/nodejs-icon.svg';
	import reactIcon from '../lib/assets/react-icon.svg';
	import svelteIcon from '../lib/assets/svelte-icon.svg';
	import golangIcon from '../lib/assets/golang-icon.svg';
	import postgresqlIcon from '../lib/assets/postgresql.svg';
	import tailwindcssIcon from '../lib/assets/tailwindcss-icon.svg';
	import pythonIcon from '../lib/assets/python-icon.svg';
	import flaskIcon from '../lib/assets/flask-icon.svg';
	import djangoIcon from '../lib/assets/django-icon.svg';
	import dockerIcon from '../lib/assets/docker-icon.svg';
	import wailsIcon from '../lib/assets/wails-icon.svg';
	import solidIcon from '../lib/assets/solidjs-icon.svg';

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
	<p class="text-lg font-medium text-white">Tech</p>
	<div class="flex flex-col gap-2">
		<div class="flex flex-wrap gap-10">
			<img src={nextIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={reactIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={solidIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={svelteIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={nodejsIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={golangIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={postgresqlIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={tailwindcssIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={pythonIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={flaskIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={djangoIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={wailsIcon} alt="nextjs-icon" width={40} height={40} />
			<img src={dockerIcon} alt="nextjs-icon" width={40} height={40} />
		</div>
	</div>
</Block>
