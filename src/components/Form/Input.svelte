<script lang="ts">
	import { createEventDispatcher } from 'svelte'
	export let value: '0' | '1' = '0'
	export let forcusFormId = 0
	export let formId = 0

	let input
	const dispatch = createEventDispatcher()

	const onInput = (e: Event & {
    currentTarget: EventTarget & HTMLInputElement
	}) => {
		const targetValue = e.currentTarget.value

		if (String(targetValue) === '0' || String(targetValue) === '1') {
			value = String(targetValue) as '0'| '1'
		} else {
			value = null
		}
		dispatch('onInput', formId)
	}

	$: {
		if (forcusFormId === formId && input) {
			console.log(input)
			input.focus()
		}
	}
</script>

<input
	value={value}
	on:input={(e) => onInput(e)}
	type="text"
	class="input"
	maxlength="1"
	bind:this={input}
>
{formId}
{forcusFormId}
<style>
	.input {
		width: 80px;
		height: 80px;
		font-size: 50px;
		text-align: center;
		border: 1.5px solid rgb(137, 137, 137);
	}
</style>