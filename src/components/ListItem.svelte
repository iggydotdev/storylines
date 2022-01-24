<script>
	export let data;
	function changeItem(value){
		console.log(`change item. Category: ${value}`);
		//'should pass ()'category, item id');
		// filter from inventory for category and return
	};
</script>
<button on:click={()=>changeItem(data.label)}>
	<div class='card'>
		<div class='header'>{data.label}</div>
		<div class='content'>
			<div class='content-image mr1 mt1'>
				<img src={data.imgSrc} alt=''/>
			</div>
			<div class='content-info'>
				<div class='item-name '>
					{data.name}
				</div>
				<div class='item-stats'>
					<ul class='list pa0'>
						{#each Object.entries(data.stats) as stat}
						<li>{stat[0]}: {stat[1]}</li>
						{/each} 
					</ul>
				</div>
			</div>
	  </div>
  </div>
</button>
<style>
	* {
		font-family: "VT323";
	}
	button {
		background: transparent;
		border: 0;
		padding:0;
		margin:0;
	}
	.card {
		background: white;
		width: auto;
		display:flex;
		flex-flow: column;
		flex: 1 1 auto;
		width: auto;
		margin-right: 1px;
	}
	.header {
		display: flex;
		border: 2px solid black;
		color: white;
		background: #aaa;
		margin-bottom: 0px;	
	}
	
	.content {
		margin-top: -1px;
		border: 2px solid black;
		background: white;
		padding: 2px;
		display: flex;	
	}
	.content-image {
		height: 100%;
		width: auto;
	}
	.content-info {
		background: #333;
		color:white;
		padding: 2px;
		display: flex;
		flex-flow: column wrap;
	}
	
</style>
