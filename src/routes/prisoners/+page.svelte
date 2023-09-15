<script>
  import * as prismic from "@prismicio/client";
  import { SliceZone } from "@prismicio/svelte";
  import { components } from "$lib/slices";

  export let data;

  //MOVE PRISONERS FUNCTION//
  let prisoners = data.list;
  console.log(data.list);
  console.log(prisoners.length);

  let index = 0;

  const nextPrisoner = () => {
    index = (index + 1) % prisoners.length;
  };

  const previousPrisoner = () => {
    if (index != 0) {
      index = (index - 1) % prisoners.length;
    } else {
      index = prisoners.length - 1;
    }
  };
</script>

<section>
  <h2>
    {@html prismic.asHTML(prisoners[index].data.name)}
  </h2>

  <button on:click={previousPrisoner}>
    <img src="/arrow-left.svg" alt="button to move to previous prisoner" />
  </button>

  <div class="prisoner">
    <img
      class="person-head"
      src={prisoners[index].data.image.url}
      alt="prisoner"
    />
    <img
      class="person-body"
      src="./person-prison-body.png"
      alt="prisoner-body"
    />
  </div>

  <button on:click={nextPrisoner}>
    <img src="/arrow-right.svg" alt="button to move to next prisoner" />
  </button>
</section>

<style>
  section {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    width: 100vw;
    height: 100vh;
    background: url("./prisoncell.png");
    background-size: cover;
    background-position: center;
  }

  h2 {
    position: absolute;
    text-align: center;
    width: 100%;
  }

  button {
    text-decoration: none;
    background-color: transparent;
    border: none;
    outline: none;
    z-index: 10;
  }

  .prisoner {
    position: relative;
    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 40vw;
    height: 50vh;
  }

  .person-head {
    position: absolute;
    top: 20px;
    width: 150px;
  }

  .person-body {
    width: 200px;
  }
</style>
