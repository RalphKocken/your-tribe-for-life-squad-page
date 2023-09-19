<script>
  import * as prismic from "@prismicio/client";
  import { SliceZone } from "@prismicio/svelte";
  import { components } from "$lib/slices";

  export let data;

  // JAVA SCRIPT

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

<!-- HTML -->


<section>
  <div class="button-return-container">
    <button class="button-return"><a href="/creators">Return</a></button>
  </div>


  <div class="flex-container-prisoners">

  <h2>
    {@html prismic.asHTML(prisoners[index].data.name)}
  </h2>


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

  </div>

  <button on:click={previousPrisoner}>
    <img src="/arrow-left.svg" alt="button to move to previous prisoner" />
  </button>

  <button on:click={nextPrisoner}>
    <img src="/arrow-right.svg" alt="button to move to next prisoner" />
  </button>
</section>


<!-- CSS -->
<style>
  h2 {
    position: absolute;
    text-align: center;
    width: 100%;
  }

  section {
    width: 100vw;
    height: 100vh;
    background: url("./prisoncell.png");
    background-size: cover;
    background-position: center;
    overflow: hidden;
  }

  .flex-container-prisoners {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    position: relative;
  }

  .button-return-container{


  }

  a {
    text-decoration: none;
    color: black;
  }

  .button-return {
    width: 6rem;
    height: 2rem;
    background-color: #FD7A2C;
    border-radius: 5px;
    border: none;
    font-family: 'Grenze Gotisch', cursive;
    font-weight: bold;
    font-size: 1rem;
  }

  button {
    text-decoration: none;
    background-color: transparent;
    border: none;
    outline: none;
    z-index: 10;
  }

  .prisoner {
    /*position: relative;*/
    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: center;
    /*width: 40vw;*/
    /*height: 50vh;*/
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
