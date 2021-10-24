<script>
    import { createEventDispatcher } from 'svelte';

    let task = {
        name: '',
        completed: false
    };
    const dispatch = createEventDispatcher();

    const handleAddTask = (event) => {
        event.preventDefault();
        dispatch('addatask', task);
        task = { name: '', completed: false };
    }
</script>

<form on:submit={handleAddTask}>
    <div class="field">
        <label for="taskname">Nombre de la tarea</label>
        <input required name="taskname" type="text" bind:value={task.name}>
    </div>
    <div class="field">
        <label for="completed">Estado de la tarea</label>
        <input type="checkbox" name="completed" bind:checked={task.completed}>
    </div>
    <div class="field">
        <input type="submit" value="Añadir tarea">
    </div> 
</form>

<style>
    .field {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
    }
    input {
        margin: 0;
    }
    label {
        margin-right: 10px;
    }
</style>