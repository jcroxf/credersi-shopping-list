<script>
    import {createEventDispatcher} from 'svelte';
    import {v4 as uuidv4} from 'uuid';

    const dispatch = createEventDispatcher();
    let newItemText = "";

    const onCreate = () => {
        dispatch('create', {text: newItemText, uuid: uuidv4()});
        newItemText = "";
    };

    const onKeyPress = (event) => {
        if (event.charCode === 13) {
            onCreate();
        }
    };
</script>

<style type="text/scss">
	@import 'src/styles/vars';

    button {
        flex-grow: 0;
    }

    input {
        flex-grow: 1;
    }

    component {
        display: flex;
        flex-direction: row;
        gap: $padding;
        padding: $padding;
    }
</style>

<component>
    <input bind:value={newItemText} id="new-item" name="new-item" on:keypress={onKeyPress} type="text">
    <button id="create-item" on:click={onCreate}>Create</button>
</component>
