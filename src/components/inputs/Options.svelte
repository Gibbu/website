<script>
	import {createEventDispatcher} from 'svelte';
	const dispatch = createEventDispatcher();

	// Components
	import {Select} from '$components/common';

	// Required input vars
	export let variable: string;
	export let options: {title: string, value: string}[];
	export let value: string;
	export let title: string;

	// Optional input vars
	export let hint: string = '';
	export let customValue = true;
	export let addon = false;

	const update = ({detail: value}) => {
		dispatch('update', {variable, value, addon});
	}
</script>

<header class="option-header">
	<p class="option-title">{title}</p>
	{#if hint}
		<small class="option-hint">{hint}</small>
	{/if}
</header>
<div class="option-body">
	<Select {options} {value} {customValue} on:update={update} />
</div>