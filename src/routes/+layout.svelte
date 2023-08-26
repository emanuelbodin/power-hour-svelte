<script>
	import BottomNavigation from '$lib/components/bottom-navigation.svelte'
	import './styles.css'
</script>

<div class="app">
	<main class="min-h-screen bg-gradient-to-br from-slate-900 to-slate-700">
		<slot />
	</main>
	<BottomNavigation />
</div>
