<script lang="ts"></script>

<nav>
	<div id="wrapper">
		<ul>
			<li>
				<a href="/"
					><img
						src="./images/logo.svg"
						alt="a logo that sort of looks like the letter 'm'"
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
