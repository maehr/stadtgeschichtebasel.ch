<script lang="ts">
	// https://www.skeleton.dev/components/tables
	import { Table } from '@skeletonlabs/skeleton';
	import type { TableSource } from '@skeletonlabs/skeleton';
	import { tableMapperValues } from '@skeletonlabs/skeleton';
    import Container from '$lib/components/Container.svelte';
	/** @type {import('./$types').PageData} */
    export let data;
    const sourceData = data.features.map((feature) => {
        return {
            name: feature.properties.name,
            description: feature.properties.description,
            address: feature.properties.address,
            website: feature.properties.website
        };
    });
    const tableSimple: TableSource = {
		// A list of heading labels.
		head: ['Ort', 'Beschreibung', 'Addresse', 'Website'],
		// The data visibly shown in your table body UI.
		body: tableMapperValues(sourceData, ['name', 'description', 'address', 'website']),
		// Optional: The data returned when interactive is enabled and a row is clicked.
		meta: tableMapperValues(sourceData, ['position', 'name', 'symbol', 'weight']),
	};

	import * as config from '$lib/config';
</script>

<Container>
	<h1>Orte</h1>
	<p>
		Unsere Kollaborationspartner*innen finden Sie hier.
	</p>
	
</Container>
<Table source={tableSimple} interactive={true}  />
