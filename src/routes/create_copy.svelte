
<script>
    import ProgressBar from "../components/ProgressBar.svelte";
    import Form from '../components/Form.svelte';

    let steps = ['Info', 'Address', 'Payment', 'Confirmation'], currentActive = 1, progressBar;

    const handleProgress = (stepIncrement) => {
        progressBar.handleProgress(stepIncrement)
    }
</script>

<div class="w-full h-screen flex flex-col items-center">
    <div class="w-[800px]">
    <div class="my-16 w-max">
        <h1 class="text-6xl font-playfair">let's make a playlist</h1>
        <div class="typewriter my-6">
            <p class="font-mono font-bold text-orange-600 text-2xl w-max">Change each attribute to get a cool playlist...</p>
        </div>
    </div>
    </div>

    <ProgressBar {steps} bind:currentActive bind:this={progressBar}/>

    <div class="flex flex-row items-center justify-center gap-12 w-[800px]">
        <button class="block md:inline-block" on:click={() => handleProgress(-1)} disabled={currentActive == 1}>
            <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg" fill-rule="evenodd" clip-rule="evenodd"><path d="M20 .755l-14.374 11.245 14.374 11.219-.619.781-15.381-12 15.391-12 .609.755z"/></svg>
        </button>

        <Form active_step={steps[currentActive-1]}/>
        
        <button class="block md:inline-block" on:click={() => handleProgress(+1)} disabled={currentActive == steps.length}>
            <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg" fill-rule="evenodd" clip-rule="evenodd"><path d="M4 .755l14.374 11.245-14.374 11.219.619.781 15.381-12-15.391-12-.609.755z"/></svg>
        </button>
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