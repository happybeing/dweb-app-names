<script>
import { onMount } from 'svelte';

let names = $state();
let new_name = $state('');
let new_address = $state('');
let get_list_error = $state('');
let add_name_error = $state('');

async function get_list_names() {
	clearErrorMessage();
	const response = await fetch('http://127.0.0.1:8080/dweb/v0/name-list');
	if (response.status == 200) {
		let all_names = await response.json();
		let a = ""; let b = "";
		// @ts-ignore
		names = all_names.sort((a, b) => (a.key > b.key) ? 1 : -1)
	} else {
		get_list_error = "Error: failed to get names from server"
	}
}

async function add_a_name() {
	clearErrorMessage();
	let url = 'http://127.0.0.1:8080/dweb/v0/name-register/' + new_name + '/' + new_address;
	const response = await fetch(url);
	if (response.status == 200) {
		await response.text();
		await get_list_names();
	} else {
		add_name_error = "Error: server failed to add name " + "'" + new_name + "'";
	}
}

function clearErrorMessage() {
	get_list_error = '';
	add_name_error = '';
}

const handleKeypress = (/** @type {{ key: string; }} */ event) => {
	if (event.key == 'Enter') {
		add_a_name();
	}
}

onMount(() => {
     get_list_names();
})
</script>

<h2>current names</h2>
<table><tbody>
{#each names as name}
	<tr><td>{name.key}</td><td>{name.history_address}</td></tr>
	{/each}
</tbody></table>
<p class='error'>{get_list_error}</p>

<h2>add a name</h2>
<div>
	<input placeholder="<DWEB-NAME>" bind:value={new_name} onkeypress={handleKeypress} />
	<input placeholder="<HISTORY-ADDRESS>" bind:value={new_address} onkeypress={handleKeypress} />
	press Enter to add
</div>
<p class='error'>{add_name_error}</p>
<p></p>
<table><tbody>
<tr><td>&lt;DWEB-NAME&gt;</td><td></td><td>
A short name for the site at HISTORY-ADDRESS</td></tr>

<tr><td>&lt;HISTORY-ADDRESS&gt;</td><td></td><td>
The address of a directory or website history on Autonomi</td></tr>
</tbody></table>

<!-- <button onclick={get_list_names}>Update names</button> -->

<style>
	.error {
		color: red;
	}
</style>
