<script>
	let WIFI_SSID = "";
	let WIFI_password = "";
	let token = "";
	let config={};
	let todos = [
		{ done: false, text: 'EnablePwmOut' },
		{ done: false, text: 'EnableSensorAnalog' },
		{ done: false, text: 'EnableSensorBme280' },
		{ done: false, text: 'EnableSensorSht20' },
		{ done: false, text: 'EnableSensorBmp280' },
		{ done: false, text: 'EnableSensorCcs811' },
		{ done: false, text: 'EnableSensorDallas' },
		{ done: false, text: 'EnableSensorDht' },
		{ done: false, text: 'EnableSensorPzem' },
		{ done: false, text: 'EnableSensorUltrasonic' },
		{ done: false, text: 'EnableSensorUptime' },
		{ done: false, text: 'EnableSensorAny' },
		{ done: false, text: 'EnableTelegram' },
		{ done: false, text: 'EnableUart' }
	];

	function add() {
		todos = todos.concat({ done: false, text: '' });
	}

	function clear() {
		todos = todos.filter(t => !t.done);
	}

	$: remaining = todos.filter(t => !t.done).length;
	
	// ------- ?@>3@5AA10@ ---------
	function move(){
  var elem = document.getElementById("greenBar");
	var width = Math.round ((14 - remaining)/14*100);
				elem.style.width = width + '%';  
				elem.innerHTML = width * 1  + '%';

		config["token"] = token; 
		config["WIFI_SSID"] = WIFI_SSID; 
		config["WIFI_password"] = WIFI_password; 
		todos.forEach(function(item, i, arr) {
 			config[item.text] = item.done==true? 1:0   ; 
	});
		 console.log(config);
		
}
	// ------- ?@>3@5AA10@ ---------
</script>



 <div id="greyProgress">
  <div id="greenBar">0%</div>
</div>
<br>
<!-- <button on:click={move}>0<OBL</button><br>-->
<input 	on:change={move}		
			placeholder="8F5=78O"
			bind:value={token}
			>
{#if token==''}
	C?8BL ;8F5=78N
{/if}
<br>
<input 	on:change={move}		
			placeholder="WIFI_SSID"
			bind:value={WIFI_SSID}
			>
<input	on:change={move}		
			placeholder="WIFI_password"
			bind:value={WIFI_password}
			><br>


{#each todos as todo}
	<div>
		<input
			type=checkbox
			bind:checked={todo.done}
			on:change={move}		 
		>
		<lable>{todo.text}</lable>
<!--		<input
			placeholder="'B> =04> A45;0BL?"
			bind:value={todo.text}
			disabled={todo.done}
		>  
-->
	</div>
{/each}

<p>AB0;>AL: {remaining}</p>

   <form action="fwbuilder.php" method="post" name="fwbuilder" >
		 <input hidden type="text" name="config" bind:value={config} />
		 <input type="submit" name="send" value="A>1@0BL ?@>H82:C">
</form>
<!--	<button on:click={add}>
	>20O
</button>


<button on:click={clear}>
	#1@0BL 7025@H5==K5
</button>



{JSON.stringify(config)}
-->
<style>
 #greyProgress {
  width: 100%;
  background-color: #ddd;
}
	#greenBar {
  width: 0%;
  height: 20px;
  background-color: #4CAF50;
  text-align: center;
  line-height: 20px;
  color: white;
}
</style>