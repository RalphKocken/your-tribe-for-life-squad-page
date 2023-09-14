<script>
    import * as prismic from '@prismicio/client'
    import { SliceZone } from '@prismicio/svelte'
    import { components } from '$lib/slices'

    export let data

    //MOVE PRISONERS FUNCTION//
    let prisoners = data.list
    console.log(data.list)
    console.log(prisoners.length)

    let index = 0
    
    const nextPrisoner = () =>{
        index = (index + 1) % prisoners.length
    }

    const previousPrisoner = () => {
    if (index != 0) {
      index = (index - 1) % prisoners.length;
    } else {
      index = prisoners.length - 1;
    }
    };
</script>

<section>
    <button on:click={previousPrisoner}>
        <img src="/arrow-left.svg" alt="button to move to previous prisoner">
    </button>
    <div class="prisoner">
        <h2>
            {@html prismic.asHTML(prisoners[index].data.name)}
        </h2>
    </div>
    <button on:click={nextPrisoner}>
        <img src="/arrow-right.svg" alt="button to move to next prisoner">
    </button>
</section>

<style>
    section{
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 4rem;
        background-color: black;
        background: url("./prisoncell.png");
        background-size: cover;
        background-position: center;
    }

    h2{
        width: 100px;
        text-align: center;
    }

    button{
        text-decoration: none;
        background-color: transparent;
        border: none;
        outline: none;
    }

</style>