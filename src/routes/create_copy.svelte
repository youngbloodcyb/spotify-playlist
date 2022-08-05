
<script>
    import ProgressBar from "../components/ProgressBar.svelte";

    let steps = ['test', 'test', 'test', 'test', 'test', 'test', 'test'], currentActive = 1, progressBar;

    const handleProgress = (stepIncrement) => {
        progressBar.handleProgress(stepIncrement)
    }
</script>

<div class="w-full h-screen flex flex-col items-center">
    <div class="my-16 w-max">
        <h1 class="text-6xl font-playfair">let's make a playlist</h1>
        <div class="typewriter my-6">
            <p class="font-mono font-bold text-orange-600 text-2xl w-max">Select the genre that you want to make a playlist of</p>
        </div>
    </div>
    <ProgressBar {steps} bind:currentActive bind:this={progressBar}/>
    <div class="font-mono">
        <button class="p-3 transition-all duration-300 ease-in-out font-mono border-black border-solid border-2 rounded-none  hover:shadow-[-6px_6px_#000] block md:inline-block my-4 hover:text-orange-600 hover:text-bold w-full sm:w-40 text-center" on:click={() => handleProgress(-1)} disabled={currentActive == 1}>Prev</button>
        <button class="p-3 transition-all duration-300 ease-in-out font-mono border-black border-solid border-2 rounded-none  hover:shadow-[-6px_6px_#000] block md:inline-block my-4 hover:text-orange-600 hover:text-bold w-full sm:w-40 text-center" on:click={() => handleProgress(+1)} disabled={currentActive == steps.length}>Next</button>
    </div>
    
</div>

<style>
    .typewriter p {
        overflow: hidden; /* Ensures the content is not revealed until the animation */
        border-right: .15em solid rgb(234 88 12); /* The typwriter cursor */
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
        50% { border-color: rgb(234 88 12); }
    }
</style>