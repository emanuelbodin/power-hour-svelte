<script lang="ts">
	import Timer from '$lib/components/timer.svelte'
	import tupp from '$lib/images/tupp.svg'
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="flex flex-col gap-4 justify-center items-center p-4">
	<img class="w-1/3" src={tupp} alt="tupp" />
	<Timer />
</section>
