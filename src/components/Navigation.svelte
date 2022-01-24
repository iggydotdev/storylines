<script>
	import { selection } from '../data/stores.js';
	
	let userAuth = true 
	let selected = 'map';
</script>
<nav class="bg-white">
	<ul class="list flex items-center justify-around pa0 ma0">
		<li class="">
			<a class:active="{selected==='map'}" href='/map' on:click|preventDefault={()=>{selected='map';selection.set('map');}} class="black no-underline h2 f4"> 
				Map 
			</a>
		</li>
		{#if userAuth}
			<li class="">
				<a class:active="{selected === 'basement'}" href='/basement' on:click|preventDefault={()=>{selected='basement';selection.set('basement');}} class="black no-underline h2 f4"> 
					Basement
				</a>
			</li>
			<li class="">
				<button on:click={()=>console.log('logout')} class="pa0 ma0 br0 b--none bg-white black h2 f4 ma0 pa0">
					Logout
				</button>
			</li>
		{:else}
			<li class=""><a href='/login' class="white no-underline h2 f4"> Login</a></li>
		{/if}
	</ul>
</nav>

<style>
	.active {
		text-decoration: underline;
	}
</style>
