<script>
    import * as prismic from '@prismicio/client'
    import { SliceZone } from '@prismicio/svelte'
    import { components } from '$lib/slices'
  
    export let data
    let members = data.list
  </script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

{#each members as member }
  <!-- <h1>{ member.name}</h1 > -->

  {@html prismic.asHTML(member.data.name)}
  <a href={member.data.link}>Visitekaartje</a>

  {/each}