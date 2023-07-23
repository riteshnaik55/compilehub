<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p>This website is created by Ritesh Naik. Feel free to contact @ 
			<a href="https://linkedin.com/in/riteshnaik55" target="_blank">LinkedIn</a>
			<a href="https://github.com/riteshnaik55" target="_blank">Github</a> 
		</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		min-width: 100%;
		margin: 0 auto;
		box-sizing: border-box;
		
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background:#000c91;
		color:rgb(255, 255, 255);
		font-size: large;
		margin-top: 15px;
	}

	footer a {
		font-weight: bold;
		color:rgb(255, 251, 0);
	}

</style>
