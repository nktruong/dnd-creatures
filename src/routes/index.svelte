<script>
  // 1. on click ->  program fetches DND 5e API
  // 2. program chooses a random # -> accesses a creature's object
  // 3. with creature index -> fetches again to find info
  // 4. use formatting to display content

  let promise = Promise.resolve()

  async function getMonster(){
    let randomNum = getRandomInt()

    const response = await fetch("https://www.dnd5eapi.co/api/monsters/")
    const data = await response.json()

    if (response.ok){
      return data.results[randomNum]
    } else {
      throw new Error(data)
    }
  }

  function getRandomInt(){
    return Math.floor(Math.random() * 332)
  }

  function handleClick(){
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
    <button on:click={ handleClick } type="button" class="bg-gray-700 text-gray-200 py-1 px-3 rounded-sm text-2xl">Roll</button>
  </section>
</main>

<!-- Houses the content -->
<section> 
  {#await promise}
    <p>Waiting ...</p>
  {:then data}
    <p>{JSON.stringify(data)}</p>
  {:catch error}
    <p class="text-red-600 text-2xl">{error.message}</p>
  {/await}
</section>
