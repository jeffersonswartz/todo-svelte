<script>
    let todoList = [{
        complete: false,
        task: 'First'
    }];
    let newTodo = '';
    function addTodo() {
        newTodo ? todoList = todoList.concat([{completed: false, task: newTodo}]) : false;
        newTodo = '';
    }

    $: completedTasks = todoList.filter(todo => todo.complete);
</script>

<style>

</style>

<h1>Todo Component</h1>
<div>
    <h4>Add a Todo</h4>
    <input type="text" bind:value={newTodo}>
    <button on:click={addTodo}>Add Todo</button>
</div>

<h2>Work to be Done</h2>

<div>
    {#each todoList as todo}
        <div>
            <input type=checkbox value={todo.complete}>
            <input bind:value={todo.task}>
        </div>
    {/each}
</div>

<div>
    {#if completedTasks.length === 0}
        <div>
            Do Some Work !
        </div>
    {:else}
        {#each completedTasks as task}
            <div>
                {task.task}
            </div>
        {/each}
    {/if}
</div>