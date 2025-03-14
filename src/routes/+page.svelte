<script>
</script>
<svelte:head>
	<title>a dweb names app on Autonomim</title>
	<meta name="description" content="adweb names app on Autonomi" />
</svelte:head>

<div class="text-column">
	<h1>a dweb names app on Autonomi</h1>
		Welcome to the <strong>names</strong> SvelteKit app on the Autonomi peer-to-peer network.

	<p>
		This example uses the following dweb APIs to list and
		create dweb names:
	</p>
		<ul>
			<strong>/dweb/v0/name-list</strong><br/>
			<strong>/dweb/v0/name-register</strong>
		</ul>
    <p>The names are stored in your localhost dweb server and can be used in a
        browser or with the dweb command line app, to open websites on Autonomi.
    </p>
	<p>You can use dweb APIs to create interactive apps for
		Autonomi using any web tooling that generates
		static HTML. But SvelteKit is the best!</p>
</div>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
