<script>
    import Item from 'components/Item.svelte';

    export let items = [];
</script>

<style type="text/scss">
	@import 'src/styles/vars';

    component {
        display: flex;
        flex-direction: column;
        padding-left: $padding*3;
    }
</style>

<component>
    {#each items as item, index}
        <Item on:done {index} {item}/>
    {/each}
</component>
