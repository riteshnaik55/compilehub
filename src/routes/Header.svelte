<script>
	import logo from '$lib/images/code.png';
</script>

<header>
	<div class="corner">
		<a href="/">
			<img src="{logo}" alt="Logo"/>
			Compile Hub
		</a>		
	</div>

	<nav>
		<ul>
			<li>
				<a href="/">Home</a>
			</li>
			<li>
				<a href="/compile">Compiler</a>
			</li>
			<li>
				<a href="/about">About</a>
			</li>
		</ul>
	</nav>
</header>

<style>
	header {
		display: flex;
		justify-content:space-between;
		background-color: rgb(60, 10, 126);
		position: sticky;
		padding:10px;
	}
	.corner {
		height: 3em;
	}
	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		color: rgb(255, 255, 255);
		text-decoration: none;
		font-size: 1.5rem;
		margin-left: 15px;
	}
	.corner a:hover{
		color: aliceblue;
	}
	.corner img{
		width:2rem;
		height:2rem;
		padding-right: 5px;
	}
	nav {
		display: flex;
		justify-content: left;
		padding-right: 40px;
	}
	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}
	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color:rgb(255, 255, 255);
		font-weight: 700;
		font-size: 1rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}
	a:hover {
		color: var(--color-theme-1);
	}
</style>
