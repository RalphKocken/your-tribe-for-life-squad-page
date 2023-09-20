<script>
    import * as prismic from "@prismicio/client";
    import {SliceZone} from "@prismicio/svelte";
    import {components} from "$lib/slices";
    import { onMount } from "svelte";

    export let data;

    // JAVA SCRIPT

    //MOVE PRISONERS FUNCTION//
    let prisoners = data.list;
    console.log(data.list);

    let index = 0;

    const nextPrisoner = () => {
        index = (index + 1) % prisoners.length;
    };

    const previousPrisoner = () => {
        if (index != 0) {
            index = (index - 1) % prisoners.length;
            console.log(index)
        } else {
            index = prisoners.length - 1;
        }
    };

    
    onMount(() => {
        console.log(prisoners[17])
        window.addEventListener('click', () =>{
            const personHead = document.querySelector(".prisoner")
            const personImage = document.querySelector('.person-head')
            let personValue = personHead.getAttribute("value")
            console.log(personValue)
                    if(personValue === 'danique'){
                        personImage.style.marginTop = "60px"
                    }else if(personValue === 'sanne'){
                        personImage.style.marginTop = "20px"
                    }else if (personValue === 'maaike'){
                        personImage.style.marginTop = "40px"
                    }else{
                        personImage.style.marginTop = '0px'
                    }
    });
    });




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
        <a href="{ prisoners[index].data.link.url }">  
        <div class="prisoner" value="{prisoners[index].uid}">
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
        </a>
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
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

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
        top: 35vh
    }

    .button-container-next-previous {
        position: absolute;
        top: 85vh;
        left: 20vh;
    }

    .button-container-next-previous button {
        text-decoration: none;
        background-color: transparent;
        border: none;
        outline: none;
    }

    /* MEDIA QUERY TABLET */
    @media screen and (min-width: 768px) and (max-width: 1024px) {

        h2 {
            font-size: 3rem;
        }

        .person-head {
            width: 300px;
            top: 25vh;
        }

        .person-body {
            width: 550px;
            top: 33vh
        }

        .button-container-next-previous {
            left: 32vh;
        }
    }

    /* MEDIA QUERY DESKTOP */
    @media screen and (min-width: 1025px) {

        h2 {
            font-size: 4rem;
            
        }

        .person-head {
            width: 400px;
            top: 15vh;
        }

        .person-body {
            width: 850px;
            top: 23vh
        }

        .button-container-next-previous {
            left: 86.5vh;
            padding-top: 3rem;
        }

    }

</style>
