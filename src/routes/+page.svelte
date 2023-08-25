<script lang='ts'>
	import Timer from '$lib/components/timer.svelte';
	import tupp from '$lib/images/tupp.svg'
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class='flex flex-col gap-2 justify-center items-center'>
	<picture>
		<source srcset={tupp} type="image/webp" />
		<img src={tupp} alt="Welcome" />
	</picture>
	<Timer/>
</section>
