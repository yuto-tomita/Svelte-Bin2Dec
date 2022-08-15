<script lang="ts">
	export let value: 0 | 1 = 0

	const onInput = (e: Event & {
    currentTarget: EventTarget & HTMLInputElement
	}) => {
		const targetValue = e.currentTarget.value

		if (Number(targetValue) === 0) {
			value = Number(targetValue) as 0
		} else {
			value = null
		}
	}
</script>

<input
	on:input={(e) => onInput(e)}
	type="text"
	class="input"
	maxlength="1"
>

<style>
	.input {
		width: 80px;
		height: 80px;
		font-size: 50px;
		text-align: center;
		border: 1.5px solid rgb(137, 137, 137);
	}
</style>