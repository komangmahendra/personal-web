<script lang="ts">
	import { onMount } from 'svelte';
	
	// component
	import BlogItem from './component/BlogItem.svelte';
	import Loading from './component/Loading.svelte';

	// type
	import type { Blog } from './component/type'

	// state
	export let blogs : Blog[] = []
	export let isLoading: boolean = false;

	onMount(async() => {
		isLoading = true

		try {
			const response = await fetch("https://api.rss2json.com/v1/api.json?rss_url=https://medium.com/feed/@mahend")
			const data = await response.json();
			blogs = data.items;
		} catch (err)
			{
				console.error(err)
			} 
		finally {
			isLoading = false
		}
	})

</script>

<main>
	<div class="main__container">
		<div class="main__profile">
			<div class="greeting__container">
				<h1> Hello, <br/>
				 I'm <span class="highlight">Komang</span></h1>
			</div>
	
			<div class="description__container">
				<p>
					I’m <span class="highlight">Front End Developer</span> at <a href="https://farmacare.id">Farmacare</a> based on Bali. 
					Previously worked in <a href="https://hellonimbly.com/">Nimbly Technologies</a>  and I have experience in network field
				</p>
			</div>


			<div class="social-media__container">
				<a href="https://github.com/komangmahendra">
					<div class="social-media__item">
						<svg fill="#000000" xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" width="32px" height="32px">    <path d="M10.9,2.1c-4.6,0.5-8.3,4.2-8.8,8.7c-0.5,4.7,2.2,8.9,6.3,10.5C8.7,21.4,9,21.2,9,20.8v-1.6c0,0-0.4,0.1-0.9,0.1 c-1.4,0-2-1.2-2.1-1.9c-0.1-0.4-0.3-0.7-0.6-1C5.1,16.3,5,16.3,5,16.2C5,16,5.3,16,5.4,16c0.6,0,1.1,0.7,1.3,1c0.5,0.8,1.1,1,1.4,1 c0.4,0,0.7-0.1,0.9-0.2c0.1-0.7,0.4-1.4,1-1.8c-2.3-0.5-4-1.8-4-4c0-1.1,0.5-2.2,1.2-3C7.1,8.8,7,8.3,7,7.6C7,7.2,7,6.6,7.3,6 c0,0,1.4,0,2.8,1.3C10.6,7.1,11.3,7,12,7s1.4,0.1,2,0.3C15.3,6,16.8,6,16.8,6C17,6.6,17,7.2,17,7.6c0,0.8-0.1,1.2-0.2,1.4 c0.7,0.8,1.2,1.8,1.2,3c0,2.2-1.7,3.5-4,4c0.6,0.5,1,1.4,1,2.3v2.6c0,0.3,0.3,0.6,0.7,0.5c3.7-1.5,6.3-5.1,6.3-9.3 C22,6.1,16.9,1.4,10.9,2.1z"/></svg>
						<span class="social-media__item-name">Github</span>
					</div>
				</a>
				<a href="https://id.linkedin.com/in/komangmahendra">
					<div class="social-media__item">
						<svg fill="#000000" xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" width="32px" height="32px">    <path d="M 5 3 C 3.895 3 3 3.895 3 5 L 3 19 C 3 20.105 3.895 21 5 21 L 19 21 C 20.105 21 21 20.105 21 19 L 21 5 C 21 3.895 20.105 3 19 3 L 5 3 z M 5 5 L 19 5 L 19 19 L 5 19 L 5 5 z M 7.7792969 6.3164062 C 6.9222969 6.3164062 6.4082031 6.8315781 6.4082031 7.5175781 C 6.4082031 8.2035781 6.9223594 8.7167969 7.6933594 8.7167969 C 8.5503594 8.7167969 9.0644531 8.2035781 9.0644531 7.5175781 C 9.0644531 6.8315781 8.5502969 6.3164062 7.7792969 6.3164062 z M 6.4765625 10 L 6.4765625 17 L 9 17 L 9 10 L 6.4765625 10 z M 11.082031 10 L 11.082031 17 L 13.605469 17 L 13.605469 13.173828 C 13.605469 12.034828 14.418109 11.871094 14.662109 11.871094 C 14.906109 11.871094 15.558594 12.115828 15.558594 13.173828 L 15.558594 17 L 18 17 L 18 13.173828 C 18 10.976828 17.023734 10 15.802734 10 C 14.581734 10 13.930469 10.406562 13.605469 10.976562 L 13.605469 10 L 11.082031 10 z"/></svg>
						<span class="social-media__item-name">LinkedIn </span>
					</div>
				</a>
				<a href="https://www.instagram.com/mahend_">
					<div class="social-media__item">
						<svg fill="#000000" xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" width="32px" height="32px">    <path d="M 8 3 C 5.243 3 3 5.243 3 8 L 3 16 C 3 18.757 5.243 21 8 21 L 16 21 C 18.757 21 21 18.757 21 16 L 21 8 C 21 5.243 18.757 3 16 3 L 8 3 z M 8 5 L 16 5 C 17.654 5 19 6.346 19 8 L 19 16 C 19 17.654 17.654 19 16 19 L 8 19 C 6.346 19 5 17.654 5 16 L 5 8 C 5 6.346 6.346 5 8 5 z M 17 6 A 1 1 0 0 0 16 7 A 1 1 0 0 0 17 8 A 1 1 0 0 0 18 7 A 1 1 0 0 0 17 6 z M 12 7 C 9.243 7 7 9.243 7 12 C 7 14.757 9.243 17 12 17 C 14.757 17 17 14.757 17 12 C 17 9.243 14.757 7 12 7 z M 12 9 C 13.654 9 15 10.346 15 12 C 15 13.654 13.654 15 12 15 C 10.346 15 9 13.654 9 12 C 9 10.346 10.346 9 12 9 z"/></svg>
						<span class="social-media__item-name">Instagram</span>
					</div>
				</a>
			</div>
		</div>
		<div class="main__posts">
			<span class="main-post__title">// POSTS</span>
			{#if isLoading}
				<div class="loading__container">
					<Loading />
				</div>
			{:else}
			<ul>
				{#each blogs as blog}
					<li><a target="_blank" href={blog.link}>
						<BlogItem blog={blog}/>
					</a></li>
				{/each}
			</ul>
			{/if}
		</div>
	</div>

	<footer class="copyright">
		<span>komang mahendra @ 2021</span>
	</footer>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;500;700&display=swap');

	:global(body) {
		background: #323437;
		font-size: 16px;
		font-family: 'Roboto', monospace;
	}

	.loading__container {
		display: flex;
		align-items: center;
		justify-content: center;
		margin-top: 5rem;
	}

	ul {
		padding: 0;
    	list-style-type: none;
	}

	li:not(:first-child){
		margin-top: 0.5rem;
	}

	a {
		text-decoration: none;
		color: white;
	}
	
	main {
		background: #323437;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 2rem;
		padding-bottom: 6rem;
	}

	.main__container {
		display: flex;
		flex-direction: column;
		width: 100%;
		max-width: 1040px;
	}

	h1 {
		font-family: 'Roboto';
		color: #D1D0C5;
		font-size: 4rem;
		font-weight: 700;
		line-height: 5rem;
		margin: 0px;
	}

	.description__container {
		margin-top: 2rem;
		letter-spacing: 1px;
	}

	.description__container a {
		color: white;
	}

	.description__container > p {
		color: #D1D0C5;
		font-size: 1.25rem;
		font-weight: 300;
		line-height: 2rem;
	}

	.main__profile {
		width: 100%;
	}

	.main__posts {
		margin-top: 5rem;
		width: calc(100% - 2rem);
		color: #D1D0C5;
	}

	.main-post__title {
		letter-spacing: 2px;
	}
	

	.highlight {
		color: #E2B714;
	}

	.social-media__container {
		display: flex;
		flex-wrap: wrap;
		margin-left: -1rem;
	}

	.social-media__item {
		display: flex;
		color: #D1D0C5;
		align-items: center;
		font-weight: 300;
		margin-left: 1rem;
		margin-top: 1rem;
	}

	.social-media__item:hover {
		color: #fff;
		text-decoration: underline;
	}

	.social-media__item > svg {
		margin-right: 0.25rem;
		fill: #D1D0C5;
	}

	.social-media__item > svg:hover {
		fill: #fff;
	}

	.copyright {
		font-size: 0.75rem;
		margin-top: 5rem;
		color: #6D6D6D;
		font-weight: 100;
	}

	@media(min-width: 960px){
		main {
			padding: 3rem;
		}

		h1 {
			font-family: 'Roboto';
			color: #D1D0C5;
			font-size: 6rem;
			font-weight: 700;
			line-height: 7rem;
			margin: 0px;
		}

		.main__profile {
			width: 50%;
		}


		.main__posts {
			margin-top: 0px;
			padding-left: 4rem;
			width: calc(50% - 4rem);
		}

		.social-media__container {
			margin-top: 5rem;
			align-items: center;
			justify-content: space-between;
			margin-left: 0px;
		}

		.social-media__item {
			margin-left: 0px;
			margin-top: 0px;
		}

		.main__container {
			flex-direction: row;
		}

	}

</style>