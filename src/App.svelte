<script>
	import Generator from 'components/Generator.svelte';
	import Shopping from 'components/Shopping.svelte';

    $: items = [
        {text: '2 pints of milk', uuid: "f1dcabef-115f-42e8-8e20-1b7b0864006e"},
        {text: 'A dozen eggs', uuid: "1bb584d4-984a-4a93-aa26-47d1c4f01e96"},
        {text: 'Nice white loaf', uuid: "8d3123e8-a7ca-47e8-a772-048ddbadb28a"}
    ];
	
	const onCreate = (event) => {
		items.unshift(event.detail);
		items = items;
	};

    const onDone = (event) => {
		let index = -1;
		for (let i = 0; ((index == -1) && (i < items.length)); i++) {
			if (items[i].uuid == event.detail.uuid) {
				index = i;
			}
		}

		if (index != -1) {
			items.splice(index, 1);
			items = items;
		}
    }
</script>

<style type="text/scss">
	@import 'src/styles/vars';

	content {
		flex-grow: 1;
		padding: $padding*2 $padding $padding $padding;
	}

	header {
		flex-grow: 0;
	}
	
	main {
		display: flex;
		flex-direction: column;
		height: 100%;
		margin-left: auto;
		margin-right: auto;
		max-width: $maxWidth;
	}

	h1 {
		display: inline;
	}

	.logo {
		float: right;
		height: $logoSize;
		width: $logoSize;
	}
</style>

<main>
	<header>
		<h1>Credersi Shopping List</h1>
		<img alt="Credersi Logo" class="logo" src="images/CredersiLogo.png"/>
	</header>
	<content>
		<Generator on:create={onCreate}/>
		<Shopping on:done={onDone} {items}/>
	</content>
</main>
