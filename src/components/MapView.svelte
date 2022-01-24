<script>
import Map from './Map.svelte';
	let position;
	function getCoordinates() {
		if (navigator.geolocation) {
			return new Promise(function (resolve, reject) {
				navigator.geolocation.getCurrentPosition(resolve, reject);
			});
		}
	}
	position = getCoordinates();
	
	
	
</script>

<section class="pa-10">
	{#await position}
		<div>Loading...</div>
	{:then data}
		<Map pos={data} />
	{:catch error}
		<div>{error.message}</div>
	{/await}
</section>

<style>
	section {
		height: 100%;
	}
</style>
