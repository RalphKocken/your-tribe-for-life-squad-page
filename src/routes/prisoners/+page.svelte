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
                        personImage.style.marginTop = "100px"
                    }else if(personValue === 'sanne'){
                        personImage.style.marginTop = "50px"
                    }else if (personValue === 'maaike'){
                        personImage.style.marginTop = "50px"
                        personImage.style.marginLeft = "10px"
                    }else if (personValue === 'wesley'){
                        personImage.style.marginTop = "30px"
                        personImage.style.marginLeft = "30px"
                    }else if (personValue === 'eliza'){
                        personImage.style.marginTop = "25px"
                        personImage.style.marginLeft = "43px"
                    }else if (personValue === 'celine'){
                        personImage.style.marginTop = "25px"
                        personImage.style.marginLeft = "13px"
                    }else if (personValue === 'anouk'){
                        personImage.style.marginTop = "25px"
                        personImage.style.marginLeft = "43px"
                    }else if (personValue === 'duneya'){
                        personImage.style.marginTop = "100px"
                        personImage.style.marginLeft = "15px"
                    }else if (personValue === 'demi'){
                        personImage.style.marginTop = "25px"
                        personImage.style.marginLeft = "10px"
                    }else{
                        personImage.style.margin = '0px'
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
        <a href="{ prisoners[index].data.link.url }" class="profile-link"> 
            Visit Profile
        </a> 
    </h2>
    
    
    <div class="flex-container-prisoners">
        
        <button on:click={previousPrisoner} class="previous-button">
            <img src="/arrow-left.svg" alt="button to move to previous prisoner"/>
        </button>

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

        <button on:click={nextPrisoner} class="next-button">
            <img src="/arrow-right.svg" alt="button to move to next prisoner"/>
        </button>

    </div>
</section>


<!-- CSS -->
<style>
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

    section {
        position: relative;
        width: 100vw;
        height: 100vh;
        background: url("/src/assets/prisoncell.png");
        background-size: cover;
        background-position: center;
        overflow: hidden;
    }

    h2{
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1rem;
        font-size: 2rem;
        text-align: center;
        z-index: 1000;
    }
    
    a {        
        text-decoration: none;
        color: black;
    }
    
    .profile-link{
        background-color: #FD7A2C;
        padding: 0.5rem;    
        border-radius: 5px;
        font-size: 1rem;
        z-index: 1000;
    }
    
    .button-return-container {
        position: absolute;
        display: flex;
        justify-content: right;
        align-items: center;
        width: 100%;
    }

    .button-return {
        border-radius: 5px;
        border: none;
        font-family: 'Grenze Gotisch', cursive;
        font-weight: bold;
        font-size: 1rem;
        z-index: 100;
        margin: 0 1vw 0 0;
    }

    .flex-container-prisoners{
        width: fit-content;
        position: absolute;
        left: 0;
        right: 0;
        bottom: 10vh;
        margin-left: auto;
        margin-right: auto;
        display: flex;
        gap: 2rem;
    }

    .flex-container-prisoners button{
        cursor: pointer;
    }
    
    .prisoner {
        position: relative;
        display: flex;
        justify-content: center;
    }

    .person-head {
        position: absolute;
        top: -120px;
        width: 280px;
        z-index: 10;
        margin: 1rem;
    }

    .person-body {
        width: 250px;
        margin: 0 auto;
    }

    button{
        background-color: transparent;
        border: none;
        z-index: 100;
    }

    button img{
        width: clamp(1rem, 4vw, 3rem);
    }


    /* MEDIA QUERY TABLET */
    @media screen and (min-width: 768px){

        .person-head {
            top: -175px;
            width: 350px;
        }

        .person-body {
            width: 300px;
        }
    }

    /* MEDIA QUERY DESKTOP */
    @media screen and (min-width: 1025px) {
        .flex-container-prisoners{
            bottom: 5vh;
        }

        .person-head {
            width: 380px;
        }

        .person-body {
            width: 350px;
        }

    }

</style>
