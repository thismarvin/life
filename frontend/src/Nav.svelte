<script lang="ts"></script>

<nav>
	<div id="wrapper">
		<ul>
			<li>
				<a href="/"
					><img
						src="./images/logo.svg"
						alt="thismarvin"
						id="logo"
						class="centered"
					/></a
				>
			</li>
		</ul>
	</div>
</nav>

<style lang="sass">
	nav
		display: flex
		align-items: center
		position: fixed
		top: 0
		overflow: hidden
		margin: auto
		padding: 0 1rem
		width: 100%
		height: 2rem
		backdrop-filter: blur(1rem)
		-webkit-backdrop-filter: blur(1rem)
		box-shadow: 0.5rem 0 1rem rgba(0, 0, 0, 0.25)
		background-color: rgba(255, 255, 255, 0.5)

	ul
		margin: 0
		padding: 0
		list-style: none

	#wrapper
		margin: auto
		width: 100%
		max-width: 1000px

	#logo
		width: 2rem
</style>
