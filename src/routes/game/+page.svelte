<script lang="ts">
	import Icon from '$lib/components/icon.svelte'
	import Timer from '$lib/components/timer.svelte'
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="flex flex-col gap-4 justify-center items-center p-4">
	<div class='w-2/3 md:w-1/3'>
		<Icon id='tupp' width='100%' height='100%' viewBox='0 0 789 585' fill='#ffc009' />
	</div>
	<Timer />
</section>
