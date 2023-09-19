<script>
    import * as prismic from "@prismicio/client";
    import {SliceZone} from "@prismicio/svelte";
    import {components} from "$lib/slices";

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

      <h2>
        {@html prismic.asHTML(prisoners[index].data.name)}
      </h2>


    <div class="flex-container-prisoners">

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

    <div class="button-container-next-previous">
        <button on:click={previousPrisoner}>
            <img src="/arrow-left.svg" alt="button to move to previous prisoner"/>
        </button>

        <button on:click={nextPrisoner}>
            <img src="/arrow-right.svg" alt="button to move to next prisoner"/>
        </button>
    </div>
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

    .button-return-container {
        display: flex;
        justify-content: center;
        align-items: center;
        padding-top: 1rem;
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

    .flex-container-prisoners {
        /*display: flex;*/
        /*flex-direction: row;*/
        /*justify-content: center;*/
        /*align-items: center;*/
        /*gap: 10rem;*/
        /*position: relative;*/
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
        width: 220px;
        top: 25vh;
        z-index: 10;
    }

    .person-body {
        position: absolute;
        width: 350px;
        top: 35vh;

    }

    .button-container-next-previous {
        position: absolute;
        top: 85vh;
        left: 20vh;
    }

    .button-container-next-previous button  {
        text-decoration: none;
        background-color: transparent;
        border: none;
        outline: none;
    }

</style>
