<script>
    import FormField from '@smui/form-field';
    import Switch from '@smui/switch';
    export let name;
    export let id;
    export let completed = false
    export let todos = []

    function removeHandler() {
        todos = todos.filter(item => item.id !== id)
        console.log(todos);
    }
</script>

<div class={`todoCardWrapper row jcsb`} id={id} >
    <strong class={`${completed && 'todoCompleted'}`}>
        {name}
    </strong>
    <div class="row">
        <FormField>
            <Switch bind:checked={completed} />
        </FormField>
        <div class="icon" on:click={removeHandler}>
            <span class="material-icons deleteIcon" >
                delete
            </span>
        </div>
    </div>
</div>

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
</style>