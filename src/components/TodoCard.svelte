<script>
    import { fade } from 'svelte/transition';
    export let todos = JSON.parse(window.localStorage.getItem('todos')) || []

    function removeHandler(e) {
        todos = todos.filter(item => {
            return  item.id !== +e.target.id
        })
        window.localStorage.setItem('todos', JSON.stringify(todos))
    }

    function checkedHandler(e, todoId) {
        let newArr = []
        todos.forEach(item => {   
            if(item.id === todoId){
                item.completed = e.target.checked
            }
            newArr.push(item)
            todos = newArr
            window.localStorage.setItem('todos', JSON.stringify(todos))
        })
    }
</script>

{#each todos as { name, id, completed }}
<div class={`todoCardWrapper row jcsb aic`} key={id} transition:fade>
    <strong class={`${completed && 'todoCompleted'}`}>
        {name}
    </strong>
    <div class="row">
        <div class="checkbox">
            <input type="checkbox" on:change={e => checkedHandler(e, id)}>
        </div>
        <div class="icon" on:click={removeHandler} id={id}>
            <span class="material-icons deleteIcon" >
                delete
            </span>
        </div>
    </div>
</div>
{/each}


<style>

    .todoCardWrapper {
        border: 1px solid #d4d4d4;
        width: 100%;
        padding: 15px 10px;
        margin-bottom: 15px;
    }
    .todoCompleted {
        text-decoration: line-through;
    }
    .icon {
        width: 40px;
        height: 40px;
        margin-left: 40px;
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .deleteIcon {
        pointer-events: none;
    }

    .checkbox {
        width: 40px;
        height: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .checkbox input{
        margin-bottom: 0;
        width: 16px;
        height: 16px;
    }
</style>