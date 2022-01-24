<script>
import { onDestroy } from 'svelte';

import Header from './components/Header.svelte';
import MapView from './components/MapView.svelte';
import Basement from './components/Basement.svelte';
import {selection} from './data/stores.js';	

let selected;

const unsubscribe = selection.subscribe(value => {
	switch (value) {
		case "basement": 
			selected = Basement; 
			break;
		default: 
			selected = MapView; 
			break;
	}
});

	onDestroy(unsubscribe);
	
</script>
<link rel="stylesheet" href="https://unpkg.com/tachyons@4.12.0/css/tachyons.min.css"/>
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"/>
<Header/>

<svelte:component this={selected}/>

<style>
	@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
	
	
	* {
		font-family: "VT323", monospace;
	}
	
</style>


