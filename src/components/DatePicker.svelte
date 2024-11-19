<script lang="ts">
  type Options = "one-way" | "return"

  function getDate() {
    const date = new Date()
    const [month, day, year] = date
      .toLocaleDateString('en-US', { year: 'numeric', month: '2-digit', day: '2-digit'})
      .split('/')

    return `${year}-${month}-${day}`
  }

  function handleSubmit(e: Event){
    e.preventDefault()
    alert(`You have booked a ${selected} flight on ${startDate}`)
  }


  let selected = $state<Options>("one-way")
  let startDate = $state(getDate())
  let returnDate = $state(getDate())

  $inspect({ selected, startDate, returnDate })
</script>

<form onsubmit={handleSubmit}>
  <select bind:value={selected}>
    <option value="one-way">One Way Flight</option>
    <option value="return">Return Flight</option>
  </select>

  <label>
    <span>Select the start date</span>
    <input type="date" bind:value={startDate} required>
  </label>

  <label>
    <span>Select the return date</span>
    <input type="date" bind:value={returnDate} disabled={selected !== 'return'} required>
  </label>

  <button type="submit" disabled={!startDate || (selected === 'return' && returnDate < startDate)}>Book flight</button>

</form>