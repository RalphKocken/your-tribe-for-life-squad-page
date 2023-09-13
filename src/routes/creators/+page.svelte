<script>
    import * as prismic from '@prismicio/client'
    import { SliceZone } from '@prismicio/svelte'
    import { components } from '$lib/slices'
  
    export let data
    let members = data.list
  </script>


<section>
  <!-- //for each loop svelte syntax// -->
  {#each members as member }
    {@html prismic.asHTML(member.data.name)}
  {/each}
  <button><a href="/prisoners">See other members</a></button>

</section>