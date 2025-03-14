<script>
	import EditNames from './EditNames.svelte';
</script>

<svelte:head>
	<title>Names</title>
	<meta name="description" content="Edit dweb Names" />
</svelte:head>

<div class="text-column">
	<h1>do stuff with dweb names</h1>
	<p>Below you can see the 'current names' known to your local dweb server and below that
		inputs so you can add new names.</p>
	<p>This is implemented by a Svelte component &lt;EditNames&gt; which uses the dweb APIs
	<strong>/dweb/v0/name-list</strong> and <strong>/dweb/v0/name-register</strong>.</p>
	<EditNames />

	<h2>using dweb names</h2>
	<p>After creating a name you will be able to open the address it refers to using the command line:</p>
	<pre>dweb open &lt;DWEB-NAME&gt;</pre>
	<p>Or you can open it directly by pasting a link into a browser, like:
	</p>
	<pre>http://127.0.0.1:8080/dweb-open/&lt;DWEB-NAME&gt;</pre>
</div>
