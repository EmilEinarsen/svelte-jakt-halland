<script>

	import { slide, fade } from 'svelte/transition'
	
	let open = false

</script>


<div class="container">

	<button on:click={() => open = !open} class:open>
		<slot name="name">
			Name...
		</slot>
	</button>

	{#if open}
	<div class="content" transition:slide="{{duration: 300}}">
		<span transition:fade="{{duration: 300}}">
			<slot>
				Content...
			</slot>
		</span>
	</div>
	{/if}

</div>


<style lang="sass">

$width: 100%

.container
	width: $width
	.content
		font-size: 20px
		width: $width
		margin: 20px 0
		padding: 0 20px
	button
		display: grid
		grid-auto-flow: column
		text-align: left
		width: $width
		padding: 6px*1.5 16px
		border-bottom: 2px solid darken(#eceff0, 20%)
		color: #223D6E
		background-color: #eceff0
		border-radius: 3px
		font-size: 15px
		transition: .01s linear

		@media (min-width: 880px)
			font-size: 20px
		
		&:hover
			cursor: pointer
			background-color: darken(#eceff0, 2.5%)

		&:active
			transform: scale(0.995)
			border-bottom: 1px solid darken(#eceff0, 10%)

		&.open::after
			transform: rotate(180deg)

		&::after
			@extend %font-awsome
			content: '\f0d7'
			font-weight: 700
			justify-self: right

%font-awsome
	display: inline-block
	font-family: 'Font Awesome 5 Free'
	font-style: normal
	font-variant: normal
	font-size: inherit
	text-rendering: auto
	-webkit-font-smoothing: antialiased

</style>