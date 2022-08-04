
<script>

</script>

<div class="w-full h-screen flex flex-row justify-center align-middle">
    <div class="my-16 w-max">
        <h1 class="text-6xl font-playfair">let's make a playlist</h1>
        <div class="typewriter my-6">
            <p class="font-mono font-bold text-orange-600 text-2xl w-max">Select the genre that you want to make a playlist of</p>
        </div>
    </div>
</div>

<style>
    .typewriter p {
        overflow: hidden; /* Ensures the content is not revealed until the animation */
        border-right: .15em solid orangered; /* The typwriter cursor */
        white-space: nowrap; /* Keeps the content on a single line */
        margin: 0; /* Gives that scrolling effect as the typing happens */
        letter-spacing: .15em; /* Adjust as needed */
        width: max-content;
        animation: 
            typing 3.5s steps(40, end),
            blink-caret .75s step-end infinite;
}

    /* The typing effect */
    @keyframes typing {
        from { width: 0 }
        to { width: 100% }
    }

    /* The typewriter cursor effect */
    @keyframes blink-caret {
        from, to { border-color: transparent }
        50% { border-color: orangered; }
    }
</style>