<script lang="ts">
  import Input from './components/Form/Input.svelte'
  
  type BinaryNumber = '0' | '1' | null
  export let inputNumbers: BinaryNumber[] = [null, null, null, null, null]
  export let forcusFormId

  const focusNextForm = (event) => {
    forcusFormId = event.detail + 1
  }

  // TODO: 独自の基数変換ロジックも書く
  $: decimalNumber = () => {
    let coalescenceNumbers = ''
    inputNumbers.forEach(val => {
      coalescenceNumbers = coalescenceNumbers + val
    })
    return parseInt(coalescenceNumbers, 2)
  }
</script>

<main>
  <h1 class="main-title">
    Bin2Dec
  </h1>

  <div class="form-label">
    Please enter binary numbers
  </div>

  <div class="form-container">
    {#each [...Array(5)] as input, i}
      <Input
        bind:value={inputNumbers[i]}
        formId={i}
        forcusFormId={forcusFormId}
        on:onInput={focusNextForm}
      />
    {/each}
  </div>

  Result

  {decimalNumber()}
</main>

<style>
.main-title {
  text-align: center;
  font-size: 2.5rem;
}

.form-label {
  text-align: center;
  margin-bottom: 20px;
  font-size: 20px;
  font-weight: bold;
}

.form-container {
  text-align: center;
}
</style>