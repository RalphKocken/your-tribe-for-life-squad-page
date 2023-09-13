<script xmlns="http://www.w3.org/1999/html">
    import * as prismic from '@prismicio/client'
    import { PrismicImage } from "@prismicio/svelte"
    import {SliceZone} from '@prismicio/svelte'
    import {components} from '$lib/slices'

    export let data
    let members = data.list
</script>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

        body {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
            font-family: 'Grenze Gotisch', cursive;
            /*background-image: url('');*/
            background-color: rgba(255, 255, 255, 0.5);
            background-size: cover;
            background-repeat: no-repeat;
            height: 100vh;
        }

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

    </style>

</head>


<section>
    <!-- //for each loop svelte syntax// -->
    {#each members as member }
        {@html prismic.asHTML(member.data.name)}
    {/each}

   <div class="button-other-members-container">
       <button class="button-other-members"><a href="/prisoners">See other members</a></button>
   </div>

</section>

<!--<div>-->
<!--<PrismicImage field={data.imageralph} />-->
<!--</div>-->

</html>


<SliceZone slices={data.slices} {components}/>



