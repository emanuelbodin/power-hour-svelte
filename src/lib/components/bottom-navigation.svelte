<script>
	import { page } from '$app/stores'
	import beerSteinWhite from '$lib/images/beer-stein-white.svg'
	import beerSteinYellow from '$lib/images/beer-stein-yellow.svg'
    import houseWhite from '$lib/images/house-white.svg'
    import houseYellow from '$lib/images/house-yellow.svg'
    import userWhite from '$lib/images/user-white.svg'
    import userYellow from '$lib/images/user-yellow.svg'

	let links = [
		{ href: '/', src: houseWhite, srcSelected: houseYellow },
		{ href: '/game', src: beerSteinWhite, srcSelected: beerSteinYellow },
		{ href: '/user', src: userWhite, srcSelected: userYellow }
	]
</script>

<div class="btm-nav">
	{#each links as link}
		<a
			href={link.href}
			class={`text-warning ${$page.url.pathname === link.href ? 'active' : ''}`}
			aria-current={$page.url.pathname === link.href}
		>
			<img src={$page.url.pathname === link.href ? link.srcSelected : link.src} alt="SvelteKit" />
		</a>
	{/each}
</div>
