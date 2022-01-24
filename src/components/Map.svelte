<script>
	import 'leaflet';
	import 'leaflet-providers';
	export let pos;
	
	function randomColor() {
		let R1 = Math.floor(Math.random()*16);
		let R2 = Math.floor(Math.random()*16);
		
		let G1 = Math.floor(Math.random()*16);
		let G2 = Math.floor(Math.random()*16);
		
		let B1 = Math.floor(Math.random()*16);
		let B2 = Math.floor(Math.random()*16);
		
		return `#${R1.toString(16)}${R2.toString(16)
		}${G1.toString(16)
		}${G2.toString(16)
		}${B1.toString(16)
		}${B2.toString(16)
		}`;
	};

	let map, user, enemy;
	pos={};
	
	// Remove this after to get the real location of the user
	user = {
				//coords: { latitude: pos.coords.latitude, longitude: pos.coords.longitude },
				// Surfers Paradise (-27.9988, 153.4224);
				coords: { latitude: -27.9988, longitude: 153.4224},
				options: {
					//	icon: userIcon,
					color: 'red',
					weight: 8,	
					fillColor: '#312232',
					fillOpacity: 0.5,
					radius: 500
				} 
			};
	
	function createMarker(newOptions) {
		return new L.Icon.extend({ 
					...newOptions
			})();
	}
	
	function addUser(map, user) {
		L.circle([user.coords.latitude, user.coords.longitude], user.options).addTo(map);
	}
	
	function battle (event) {
		console.log(e.id);
	}	
	function addMarker(map, coords, options) {
		let lat = coords.latitude;
		let lng = coords.longitude;
		L.marker([lat, lng], options)
			.addTo(map)
			.bindPopup(`pos: ${lat};${lng} tHACKER`);
	}

	function getUserOptions(coords) {
		const userColor = randomColor();
		let options = Object.assign(user.options,{color: userColor});
		return {coords,options};
	}
	
	function createMap(container) {
		try {

			let m = new L.Map(container, {
				center: new L.LatLng(user.coords.latitude, user.coords.longitude),
				zoom: 18
			});
			L.tileLayer.provider("Stamen.Toner").addTo(m);
			
			return m;
		} catch (error) {
			console.log(error);
		}
	}
	
	function mapAction(container) {
		map = createMap(container);
		return {
			destroy: () => {
				map.remove();
			}
		};
	}
	
	let base= `https://storylines.glitch.me/`;
	let URL = `${base}?latitude=${user.coords.latitude}&longitude=${user.coords.longitude}`
	fetch(URL, {method: 'POST'})
		.then(res=>res.json()).then(data =>{
			console.log(`Data: ${data}`); 		 		
			for (let ip in data) {
 				addMarker(map, data[ip], {});
				addUser(map, getUserOptions(data[ip]));
			};
		}).catch(err=>console.log(err));

	
</script>

<div class="map" use:mapAction />

<style>
	.map {
	 height: 100%;
		width: 100%;
	}
</style>
