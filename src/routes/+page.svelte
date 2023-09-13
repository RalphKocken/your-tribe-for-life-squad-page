<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">


<style>
    @import url('https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@100;200;300;400;500;600;700;800;900&display=swap');

    /* CSS */
    body {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Grenze Gotisch', cursive;
        background-image: url('src/assets/prison-image-zoom.jpeg');
        background-color: rgba(255, 255, 255, 0.5);
        background-size: cover;
        background-repeat: no-repeat;
        height: 100vh;
    }

    h1 {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 50vh;
        font-weight: bold;
        font-size: 3.5rem;
        text-align: center;
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
    }

    .button-yes, .button-no {
        width: 6rem;
        height: 2.5rem;
        background-color: #FD7A2C;
        border-radius: 5px;
        border: none;
        font-family: 'Grenze Gotisch', cursive;
        font-weight: bold;
        font-size: 1.3rem;
    }
</style>
</head>

<!--HTML -->
<body>
<section>
    <h1>Do you want to continue?</h1>
    <div class="button-container">
        <button class="button-yes"><a href="/creators">Yes</a></button>
        <button class="button-no"><a href="">No</a></button>
    </div>
</section>
</body>
</html>



