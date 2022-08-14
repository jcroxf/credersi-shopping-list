<script>
    import {createEventDispatcher} from 'svelte';
    export let index = null;
    export let item = null;
    
    const dispatch = createEventDispatcher();
    const onAction = (uuid) => dispatch('done', {uuid});
</script>

<style type="text/scss">
	@import 'src/styles/vars';

    component {
        display: flex;
        gap: $padding;
        flex-direction: row;
        padding: calc($padding/2) $padding calc($padding/2) $padding;
    }

    action {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAAXNSR0IArs4c6QAAAXhJREFUSEu9lT2Kg0AUgJ0mTYRVwVKITVQsvELIGVIFrPQQ6SbT5RCmEqw8Q8gVUojRJoGUgrqgTZpZXiBhTUJmWJi1Et6b973/hyTBH+K13zTNrOu6GejLsrxXVXXP85YJIISckiRRyrL8Go/HN/2+7+l0Ov1eLpctxtj8BHoLoJQqx+NRWSwWpyzLPjrquq6Upqlp23aLEGqflV8AVVXNVqvVLo5jdL1eebIgjUYjyfd9utls5rquD1I3AIDnYRjW2+2Wmbp35CAIaBRF2u9IBobyPJ94nnfi9fwZApEcDgfTcZzzXTYAuK5LWTln5QxqkmXZw+7jB7oFYzxhGeCRE0LO9+56ACzLaoqiUHgMsHQsy2qLolBB7waAIdI0bUcp/VNxX1oTIVrX9RyG8WbwcrmsHcfBXdexnOOSy7Is5XlODMNY/w9AeIogbqFFBoDwNgWI0EEDgPBVIXzZQRRC1/V9ioQenOdRFXIy3+0DYUefa/l8UPoBjKL2GZ+i9OwAAAAASUVORK5CYII=);
        height: $doneSize;
        margin-top: 3px;
        width: $doneSize;
    }

    action:hover {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAAXNSR0IArs4c6QAAAaJJREFUSEu11T1rVkEQBeAnRmxMEBHBIo2FRjF/IP8hRexEsBLF0hQWWuTDFHZaiWlMEwh2FpaCrdgb8mGRJlYWEjWNqJGBvbBs9r65b+Bucxfu2Tmz58zMjuh5jQwR/xzGE/4n9rucPY4gAs7hNq7iIAU9ix2s4wWCsLraCE7jMt7ixjGZbuAmdvGnxNYILuIZ7uBMFxnwG2t4jG/5mZIgMl/B3Y6BS9hrPMhvUhJcwechMm8IvuIS/mIKX5ofOUEY+rGD5mXWqynr+3iegk83xucE81gaUpp3mMU/LGAxnY/909jnBFuYHIIggkf1hCx58AixjWs5QTTR94wwDr3BLYxWSEOWe5XMG+ghzkczNjeYwCbGUkYz+IBlPCpu2iZLnscvXMfeIIL3ifBT6uLADpJlIEFNolepcU6l74VULaWhNduOSBSg0uQAvcRDxD4CxyoNrREcMTlAtTINs8OPkKtWLW1FVy3TtkaLwCHXDzzpUMYx/KqNFmdPOioa3hh6raMiQL0PuyDpdVw3V+31wcl97O3JrBVLL49+h6ocDPkPCtVvGTobaIkAAAAASUVORK5CYII=);
        cursor: pointer;
    }

    item {
        font-size: larger;
    }
</style>

<component>
    <action id="action-{index+1}"on:click={() => onAction(item.uuid)}/>
    <item data-uuid={item.uuid} id="item-{index+1}">{item.text}</item>
</component>
