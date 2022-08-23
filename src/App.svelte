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
    <Input
      bind:value={inputNumbers[0]}
      formId={0}
      forcusFormId={forcusFormId}
      on:onInput={focusNextForm}
    />
    <Input
      bind:value={inputNumbers[1]}
      formId={1}
      forcusFormId={forcusFormId}
      on:onInput={focusNextForm}
    />
    <Input
      bind:value={inputNumbers[2]}
      formId={2}
      forcusFormId={forcusFormId}
      on:onInput={focusNextForm}
    />
    <Input
      bind:value={inputNumbers[3]}
      formId={3}
      forcusFormId={forcusFormId}
      on:onInput={focusNextForm}
    />
    <Input
      bind:value={inputNumbers[4]}
      formId={4}
      forcusFormId={forcusFormId}
      on:onInput={focusNextForm}
    />
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