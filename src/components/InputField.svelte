<script>
    export let value, label, type = 'text';
  
    function typeAction(node){
      node.type = type;
    }
</script>
  
<p class="text-left">
    {#if label}
        <label class="label" for>{label}:</label>
    {/if}
    <input use:typeAction class="w-full block p-2 mt-2 border-1 rounded-none" bind:value={value}/>
</p>