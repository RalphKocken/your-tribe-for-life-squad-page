<script xmlns="http://www.w3.org/1999/html">
    import * as prismic from '@prismicio/client'
    import {PrismicImage} from "@prismicio/svelte"
    import {SliceZone} from '@prismicio/svelte'
    import {components} from '$lib/slices'

    export let data
    let members = data.list
    console.log(data.list)
</script>

<section class="creators-section">
    <!-- //for each loop svelte syntax// -->
    <div class="button-other-members-container">
        <button class="button-other-members"><a href="/prisoners">Visit other prisoners</a></button>
    </div>

    <div class="all-creators">
        {#each members as member }
            <a href="{ member.data.link.url }">       
            <div class="creator">
                {@html prismic.asHTML(member.data.name)}
                <img class="creator-image" src="{member.data.image.url}" alt="prisoner"/>
             </div>
             </a>   
        {/each}    
    </div>
</section>


<style>
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

    .creators-section {
        background-image: url('/src/assets/background-dark-prison-cell.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        height: 100vh;
        width: 100vw;
        overflow: hidden;
    }

    .button-other-members-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        margin-top: 1rem;
    }

    a {
        position: relative;
        text-decoration: none;
        color: black;
    }

    .button-other-members {
        width: 10rem;
        height: 2rem;
        background-color: #FD7A2C;
        border-radius: 5px;
        border: none;
        font-family: 'Grenze Gotisch', cursive;
        font-weight: bold;
        font-size: 1rem;
    }

    .all-creators {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: row;
        overflow-x: auto;
        text-align: center;
        font-size: 2rem;
        white-space: nowrap;
        padding-left: 2rem;
        gap: 4rem;
    }

    .creator img {
        /*width: 15rem;*/
        width: 25vh;
    }

    /* MEDIA QUERY TABLET */
    @media screen and (min-width: 768px) and (max-width: 1024px) {
        .all-creators {
            font-size: 3rem;
        }
    }

    /* MEDIA QUERY DESKTOP */
    @media screen and (min-width: 1025px) {
        .all-creators {
            justify-content: center;
            font-size: 4rem;
            margin-top: 10rem;
        }

        .creator {
            display: flex;
            flex-direction: column-reverse;
        }
    }

</style>


<SliceZone slices={data.slices} {components}/>



