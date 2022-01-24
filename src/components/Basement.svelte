<script>
	let name = 'Iggy';
	import ListItem from "./ListItem.svelte"
    import data from '../data/inventory.json'; 
	import lang from '../data/english.json';
	let stats = {
		speed: 0,
		intelligence: 0,
	};
	
</script>

<div class='basement-container'>	
<h2 class='' >{lang.basement.title}</h2>
<section>
	<h3 class='tc ma0 pt3'>
		{name}'s stats
	</h3>
	<ul class="list flex justify-around">
		{#each Object.entries(stats) as stat}
		<li>{stat[0]}:{stat[1]}</li>
	{/each}
	</ul>
	
</section>

<section>
	<h3 class='tc ma0'>Gear</h3>
		<ul class='list flex justify-around'>  
	{#each data.user.items as item}
		<li><ListItem data={item}/></li>
	{/each}
	</ul>
</section>

<section>
	<h3 class='tc ma0'>Accesories</h3>
	<ul class='list flex justify-around'>  
	{#each data.user.gear as gearitem}
		<li><ListItem data={gearitem}/></li>
	{/each}
	</ul>
</section>
</div>
<style>
	@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
	
	* {
		font-family: "VT323", monospace;
	}
	
	.basement-container {
		background: #DDD;
	}
	
	
</style>


