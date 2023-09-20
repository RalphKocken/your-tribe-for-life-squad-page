<!--Javascript-->
<script>
import { onMount} from 'svelte';

let show = false
let remove = false

</script>

<!--HTML -->
<section>
    <h1>You are about to enter the most dangerous prison in the World..</h1>
    <h2>Do you want to continue?</h2>
    <h2 class="message" class:show={show}>To late now!</h2>
    <div class="button-container">
        <button class="button-yes"><a href="/creators">Yes</a></button>
        <button class="button-no" class:remove={remove} on:click={() => [show = !show, remove = !remove]}>No</button>
    </div>
</section>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

    /* CSS */
    section{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 80%;
        height: 40vh;
        margin: 20vh auto 0 auto;
    }

    h1{
        font-size: clamp(2rem, 2vw, 3rem);
        text-align: center;
    }

    .message{
        opacity: 0;
    }

    .message.show {
        opacity: 1;
    }

    .button-no.remove{
        opacity: 0;
        pointer-events: none;
    }

    .button-container {
        display: flex;
        align-items: flex-end;
        justify-content: center;
        gap: 3rem;
        height: 30vh;
    }

    a {
        text-decoration: none;
        color: black;
        width: 100%;
        height: 100%;
    }

    .button-yes, .button-no {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 6rem;
        height: 2.5rem;
        background-color: #FD7A2C;
        border-radius: 5px;
        border: none;
        font-family: 'Grenze Gotisch', cursive;
        font-weight: bold;
        font-size: 1.3rem;
        cursor: pointer;
    }

    /* MEDIA QUERY TABLET */
    @media screen and (min-width: 768px) and (max-width: 1024px) {
        h1{
            font-size: clamp(3rem, 3vw, 4rem);
        }
    }

</style>







