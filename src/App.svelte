<script>
  import Face from "./Face.svelte"
  import Container from "./Container.svelte"
	import Header from "./Header.svelte"

	let showHeader = false

	setTimeout(() => { showHeader = true }, 1000)
</script>

{#if showHeader}
  <Header/>
{/if}

<Container>
</Container>





<style>
  /* affects styling for html in this component */
  div {
		color: red;
	}

	/* affects styling globally, for all components in this file? */
  :global(*) {
		box-sizing: border-box;
	}
	:global(body, html) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
	}
</style>
