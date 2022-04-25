<script>
  // 1. on click ->  program fetches DND 5e API
  // 2. program chooses a random # -> accesses a creature's object
  // 3. with creature index -> fetches again to find info
  // 4. use formatting to display content

  let promise = Promise.resolve()
  const monsterCount = 332

  async function getMonster(){
    // receives random number from 0 - 331
    let randomNum = getRandomInt()

    // waits for the website to return a response
    const response = await fetch("https://www.dnd5eapi.co/api/monsters/")
    const data = await response.json()

    // if successful, then it returns the data. randomNum is used to randomize which monster is chosen
    if (response.ok){
      return data.results[randomNum]
    } else {
      throw new Error(data)
    }
  }

  function getRandomInt(){
    // rounds down a random # from 0 - 331
    return Math.floor(Math.random() * monsterCount)
  }

  function handleClick(){
    // when the button is clicked, the getMonster function is set to the promise
    promise = getMonster()
  }
</script>

<main class="text-center">
  <header>
    <h1 class="font-fell text-6xl font-semibold">
      Welcome to the Creatures of DND
    </h1>
  </header>

  <section class="pt-12 font-vollkorn">
    <p class="text-xl">
      Having difficulties choosing creatures to polymorph into? Or perhaps, ones
      to roam the lands of your world?
    </p>
    <p class="py-6 text-xl italic">Then let the dice decide for you.</p>

    <!-- in Svelte, you can use the on: directive to listen for an event -->
    <button on:click={ handleClick } type="button" class="bg-gray-700 text-gray-200 py-1 px-3 rounded-sm text-2xl">Roll</button>
  </section>
</main>

<section class="text-center pt-12">
  <!-- await block to switch between waiting/resolved/error -->
  {#await promise}
    <p class="text-3xl">Waiting ...</p>
  {:then data}
    {#if data}
      <p class="text-5xl font-semibold font-elite">{data.name}</p>
    {/if}
  {:catch error}
    <p class="text-red-600 text-2xl">{error.message}</p>
  {/await}
</section>