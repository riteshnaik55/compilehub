<script>
	import back from '$lib/images/back.jpg';
	import codemulti from '$lib/images/multicode.jpg';
	import codelibrary from '$lib/images/codelibrary.jpg';
	import codeerror from '$lib/images/codeerror.jpg';
	import codecopy from '$lib/images/codecopy.jpg';

	const img={
		"Multi-language Support":codemulti,
		"Support for Standard Libraries":codelibrary,
		"Error Reporting":codeerror,
		"Shareable Code Snippets":codecopy
	}
</script>

<section class="main">
	<div class="one">
		<img src="{back}" alt="Main"/>
	</div>
	<div class="two">
		<h2>Welcome to <span>CompileHub</span></h2>
		<h3>An online compiler which allows you to compile source code and execute using 15+ programming languages.</h3>
		<a href="/compile">Open Code Compiler </a>
	</div>
</section>

<div class="features">
	<h2>Features</h2>
	<div class="container">
		{#each Object.entries(img) as [key,value]}
			<div class="card">
				<img src="{value}" alt="Code Library"/>
				<p>{key}</p>
			</div>
		{/each}
	</div>
</div>

<style>
  	@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@600&family=Poppins:wght@500&display=swap');
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
		min-height: 25rem;
		cursor:default;
	}
	h2{
		font-size: 35px;
	}
	.main{
		display: flex;
		flex-direction: row;
		background: hsla(333, 100%, 53%, 1);
		background: linear-gradient(90deg, hsla(333, 100%, 53%, 1) 0%, hsla(33, 94%, 57%, 1) 100%);
		background: -moz-linear-gradient(90deg, hsla(333, 100%, 53%, 1) 0%, hsla(33, 94%, 57%, 1) 100%);
		background: -webkit-linear-gradient(90deg, hsla(333, 100%, 53%, 1) 0%, hsla(33, 94%, 57%, 1) 100%);
		color:rgb(0, 0, 0);
		width:60rem;
		margin-left: 10rem;
		border-radius: 20px;
		box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
	}
	.features{
		margin-left: 10rem;
		border-radius: 20px;
		margin-top: 2rem;
		color:#EEFF34;
		background: hsla(261, 84%, 45%, 1);
		background: linear-gradient(90deg, hsla(261, 84%, 45%, 1) 0%, hsla(0, 93%, 22%, 1) 100%);
		background: -moz-linear-gradient(90deg, hsla(261, 84%, 45%, 1) 0%, hsla(0, 93%, 22%, 1) 100%);
		background: -webkit-linear-gradient(90deg, hsla(261, 84%, 45%, 1) 0%, hsla(0, 93%, 22%, 1) 100%);
		width:60rem;
		box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		text-align: center;
		cursor:default;
	}
	.features .container{
		width:55rem;
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		grid-gap: 50px;
		justify-items: center;
		margin: 30px auto;
		padding-bottom: 10px;
  	}
	.one img{
		width:27rem;
		height:20rem;
		padding-right: 20px;
	}
	.two h3{
		font-size: 25px;
		max-width: 28rem;
		text-align: justify;
	}
	.two span{
		color:rgb(0, 17, 255);
	}
	.two a{
		appearance: button;
		backface-visibility: hidden;
		background-color: initial;
		background-image: linear-gradient(-180deg, #00D775, #00BD68);
		border-radius: 25px;
		box-shadow: 4px 4px 1px 0px rgba(0,0,0,0.75);
		color: rgb(0, 0, 0);
		cursor: pointer;
		display: inline-block;
		font-family: Inter,-apple-system,system-ui,Roboto,"Helvetica Neue",Arial,sans-serif;
		font-size:20px;
		font-weight:bold;
		height: 44px;
		line-height: 44px;
		outline: 0;
		overflow: hidden;
		padding: 0 20px;
		pointer-events: auto;
		position: relative;
		text-align: center;
		text-transform: none;
		user-select: none;
		-webkit-user-select: none;
		vertical-align: top;
		white-space: nowrap;
		width: 13rem;
		z-index: 9;
		border: 0;
		transition: all .2s,box-shadow .08s ease-in;
		text-decoration: none;
	}
	.two a:hover{
		transform: scale(1.1);
	}
	.card {
		background:#ff9e0c;
		padding: 20px;
		border-radius: 20px;
		border: 2px solid white;
		width:20rem;
	}
	.features .card:hover{
		transform: scale(1.05);
		transition-duration: 1s;
	}
	.card p{
		font-family:'Poppins', sans-serif;
		font-weight: bold;
		font-size:20px;
		color:#320606;
	}
	.card img{
		width:5rem;
		height:5rem;		
	}
</style>
