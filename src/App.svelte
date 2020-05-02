<script>
  import Face from "./Face.svelte"
  import Container from "./Container.svelte"
	import Header from "./Header.svelte"
	import Button from "./Button.svelte"

	let showHeader = false
</script>

{#if showHeader}
  <Header/>
{/if}

<Container>

<!-- This onclick wont work without the child button -->
	<Button on:click={() => {showHeader = true}}>show</Button>

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
