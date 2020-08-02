<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
	<img alt='Success Kid' src='successkid.jpg'>
	<figcaption>Have fun with Sapper!</figcaption>
</figure>

<p><strong>{post}</strong></p>

<script context="module">
	export async function preload({ params, query }) {
	  	// the `slug` parameter is available because
	  	// this file is called [slug].html
	  	const res = await this.fetch(`https://powerful-woodland-58010.herokuapp.com/vacancies`);
	  	const data = await res.json();
		if (res.status === 200) {
			// console.log(JSON.stringify(data));
			return { post: JSON.stringify(data) };
		} else {
			this.error(res.status, data.message);
		}
	}
</script>

<script>
	export let post;
</script>