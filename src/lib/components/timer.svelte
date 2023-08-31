<script lang="ts">
	import { onMount } from 'svelte'
	enum STATE {
		NEW,
		RUNNING,
		PAUSED,
		FINISHED
	}

	let sound: HTMLAudioElement
	let state: STATE = STATE.NEW
	let interval: NodeJS.Timeout
	let shots = 0
	let timeMin = 0
	let timeSec = 0

	onMount(() => {
		sound = new Audio('tupp.wav')
	})

	const start = () => {
		if (sound) sound.play()
		shots += 1
		state = STATE.RUNNING
		interval = setInterval(() => {
			if (state !== STATE.RUNNING) return
			timeSec += 1
			if (timeSec === 60) {
				timeSec = 0
				timeMin += 1
				if (sound) sound.play()
				shots += 1
			}
			if (shots === 60) finish()
		}, 1000)
	}

	const reset = () => {
		timeSec = 0
		timeMin = 0
		shots = 0
		state = STATE.NEW
		clearInterval(interval)
	}

	const pause = () => {
		state = STATE.PAUSED
	}

	const resume = () => {
		state = STATE.RUNNING
	}

	const finish = () => {
		state = STATE.FINISHED
		clearInterval(interval)
	}

	const formatter = new Intl.DateTimeFormat('en', {
		minute: '2-digit',
		second: '2-digit'
	})

	$: elapsedTime = timeMin * 60_000 + timeSec * 1000
</script>

<div class="flex flex-col justify-center items-center gap-4">
	<div class="text-white text-2xl">{formatter.format(elapsedTime)}</div>
	<div class="text-white text-2xl">Krökbarometern: {shots}</div>
	{#if state === STATE.FINISHED}
		<p class="text-xl text-emerald-600">Finished</p>
	{/if}
	<div class="flex gap-4">
		{#if state === STATE.NEW}
			<button class="btn btn-outline btn-success w-28" on:click={start}>Start</button>
		{:else}
			<button class="btn btn-outline btn-error w-28" on:click={reset}>Reset</button>
		{/if}
		{#if state === STATE.RUNNING}
			<button class="btn btn-outline btn-warning w-28" on:click={pause}>Pause</button>
		{:else if state === STATE.PAUSED}
			<button class="btn btn-outline btn-success w-28" on:click={resume}>Resume</button>
		{/if}
	</div>
</div>
