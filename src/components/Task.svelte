<script>
    import { createEventDispatcher } from 'svelte';
    
    export let id;
    export let name;
    export let completed;

    const dispatch = createEventDispatcher();

    const handleMarkAsFinished = () => (dispatch('handlemarkfinished', { id: id }))
    const handleDelete = () => (dispatch('handledelete', { id: id }))
</script>

<div class="task">
    <div class="info">
        <p>
            {name}
            {#if completed}
                <span>Completado</span>        
            {:else}
                <span>No completado</span>      
            {/if}
        </p>
    </div>
    <div class="actions">
        <button on:click={handleMarkAsFinished}>Marcar como completado</button>
        <button on:click={handleDelete}>Borrar</button>
    </div>
</div>

<style>
    .task {
        padding: 20px;
        margin: 0 auto;
        margin-bottom: 20px;
        border: 1px dotted #333;
    }    
</style>