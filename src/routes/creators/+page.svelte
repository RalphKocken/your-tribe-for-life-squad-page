<script xmlns="http://www.w3.org/1999/html">
    import * as prismic from '@prismicio/client'
    import { PrismicImage } from "@prismicio/svelte"
    import {SliceZone} from '@prismicio/svelte'
    import {components} from '$lib/slices'
    
    export let data
    let members = data.list
    console.log(data.list)
</script>

<section>
    <!-- //for each loop svelte syntax// -->

    <div class="all-creators">
        {#each members as member }
            <div class="creator">
                {@html prismic.asHTML(member.data.name)}
                <img class="creator-image" src="{member.data.image.url}" alt="prisoner"/>
             </div>   
        {/each}    
    </div>

   <div class="button-other-members-container">
       <button class="button-other-members"><a href="/prisoners">Visit other prisoners</a></button>
   </div>

</section>



<style>
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

    a {
        text-decoration: none;
        color: black;
    }

    .button-other-members {
        width: 10rem;
        height: 2.5rem;
        background-color: #FD7A2C;
        border-radius: 5px;
        border: none;
        font-family: 'Grenze Gotisch', cursive;
        font-weight: bold;
        font-size: 1rem;
    }
    
    .all-creators{  
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .creator-image{
        height: 30vh;
    }

</style>


<SliceZone slices={data.slices} {components}/>



