<!--
A hamburger icon that animates into an close x when open
-->

<template lang='pug'>

.hamburger-button(
	:style='buttonStyle'
	:class='buttonClasses'
	@click='onClick')
	.line(
		v-for='i in 3'
		:style='lineStyle(i)')

</template>

<!-- ––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– -->

<script lang='coffee'>

# Add 'px' if value is a number
unit = (val) -> if typeof val == 'number' then "#{val}px" else val

# Module def
module.exports =

	props:

		width: # How wide to make the hamburger
			type: Number
			default: 24

		stroke: # How thick are the lines
			type: Number
			default: 2

		gap: # Space between lines
			type: Number
			default: 4

		pad: # Internal padding to make the click area bigger
			type: Number
			default: 10

		color: # The color of the lines
			type: String
			default: '#000000'

		open: # The open state
			type: Boolean
			default: false

	# Store the internal open state
	data: -> state: open: @open

	computed:

		# Styles on the button
		buttonStyle: ->
			width: unit @width + @pad * 2
			padding: unit @pad
		buttonClasses: -> open: @state.open

		# Calculate how much to shift the lines when open
		top: -> if @state.open then @gap + @stroke else 0

	# Update the internal state when the prop value changes
	watch: open: (val) -> @state.open = val

	methods:

		# Make the line styles
		lineStyle: (index) ->
			background: @color
			height: unit @stroke
			marginTop: unit @gap if index > 1
			top: switch index
				when 1 then unit @top
				when 3 then unit @top * -1

		# Handle clicks
		onClick: ->
			@state.open = !@state.open
			@$emit 'update:open', @state.open

</script>

<!-- ––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– -->

<style lang='stylus'>

// Add Bukwild functions
@import '~bukwild-stylus-library/index.styl'

.hamburger-button
	button()
	position relative

	// Add an on-down effect
	transition transform .6s ease-out-quart
	&:active
		transition-duration .3s
		transform scale(1.1)

	// The individual lines
	.line
		width 100%

		// Setup transition
		gpu-cache()
		position relative
		transition background, transform, top
		transition-duration .6s
		transition-timing-function ease-out-quart

	// Make X aout of lines
	&.open .line
		shift = 6px
		background white
		&:nth-child(1)
			transform rotate(45deg)
		&:nth-child(2)
			transform scale(0.5)
			opacity 0
		&:nth-child(3)
			transform rotate(-45deg)

</style>
