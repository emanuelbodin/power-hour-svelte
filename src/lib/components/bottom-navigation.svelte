<script>
	import { page } from '$app/stores'
	import Icon from './icon.svelte'

	let links = [
		{ href: '/',  icon: 'home' },
		{ href: '/game',  icon: 'beer' },
		{ href: '/user',  icon: 'user' }
	]
</script>

<div class="btm-nav">
	{#each links as link}
		<a
			href={link.href}
			class={`text-warning ${$page.url.pathname === link.href ? 'active' : ''}`}
			aria-current={$page.url.pathname === link.href}
		>
		<Icon id={link.icon} fill={$page.url.pathname === link.href ? '#ffc009' : '#fff'}/>
		</a>
	{/each}
</div>
