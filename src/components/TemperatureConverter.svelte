<script lang="ts">
  class Temperature {
    #c = $state(0)
    #f = $state(32)

    get c(){
      return this.#c
    }

    get f(){
      return this.#f
    }

    set c(c){
      this.#c = c
      this.#f = c * (9 / 5) + 32
    }

    set f(f){
      this.#f = f
      this.#c = (f - 32) * (5 / 9)
    }
  }

  const temperature = new Temperature()
</script>

<div class="temperature">
  <input type="number" bind:value={temperature.c}/> Celcius =
  <input type="number" bind:value={temperature.f}/> Fahrenheit
</div>