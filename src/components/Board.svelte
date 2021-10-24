<script>
    import Task from './Task.svelte';
    import AddTask from './AddTask.svelte';

    let tasks = [
        {id: 1, name: 'Tarea de prueba', completed: false}
    ];
    
    const handleAdd = (e) => {
        tasks = [...tasks, { id: tasks.length + 1, name: e.detail.name, completed: e.detail.completed }]
    }
    const handleCompleted = (e) => {
        tasks = tasks.map(task => {
            if(task.id === e.detail.id) {
                task.completed = true
            }
            return task;
        });
    }
    const handleDelete = (e) => {
        tasks = tasks.filter(f => f.id !== e.detail.id);
    }
</script>

<div class="container">    
    <div class="board">
        <AddTask on:addatask={handleAdd} />
        {#if tasks.length > 0}
            {#each tasks as { id, name, completed } }
                <Task 
                    id={id} 
                    name={name} 
                    completed={completed} 
                    on:handlemarkfinished={handleCompleted}
                    on:handledelete={handleDelete}
                />
            {/each}
        {:else}
            <p>No hay tareas</p>
        {/if}
    </div>
</div>

<style>
    .container {
        width: 100%; 
    }
    .board {
        margin: 0 auto;
        max-width: 500px;
    }
    @media screen and (max-width: 640px) {
        .board {
            max-width: none;
            margin: 0 20px;
        }
    }
</style>