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
<div class={`todoCardWrapper row jcsb aic ${completed && 'todoCompleted'}`} key={id} transition:fade>
    <input type="text" value={name} class="todoName" disabled={true}/>
    <div class="row wrapperIcons">
        <div class="checkbox">
            <input type="checkbox" on:change={e => checkedHandler(e, id)} bind:checked={completed}>
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
        transition: .3s;
        position: relative;
    }
    .todoCardWrapper::before {
        content: "";
        position: absolute;
        top: 50%;
        left: 5px;
        width: 0;
        height: 1px;
        background: #a0a0a0;
        pointer-events: none;
        transition: .3s;
    }
    .todoCardWrapper input{
        flex: 0 0 80%;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        border: none;
        outline: none;
        background: #fff;
        color: #000;
        padding-top: 9.5px;
        font-weight: 600;
    }

    .wrapperIcons {
        flex:  0 0 20%;
        justify-content: flex-end;
    }
    .todoCompleted::before {
        width: calc(100% - 10px);
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
        cursor: pointer;
        transition: .3s ease;
    }

    @media (max-width: 576px) {
        .todoCardWrapper {
           flex-direction: column;
           align-items: flex-start;
           padding: 10px 0px 0px;
        }

        .todoCardWrapper::before {
            top: 32%;
        }

        .wrapperIcons {
            width: 100%;
            justify-content: space-between;
        }

        .checkbox, .icon {
            flex: 0 0 50%;
            display: flex;
            justify-content: center;
        }

        .checkbox {
            background: #dacd23;
        }
        .icon {
            background: #c2c2c2;
            margin-left: 0;
        }

        .todoCardWrapper input.todoName {
            padding: 10px;
            width: 100%;

        }
  }
</style>