<script>
  import Face from "./Face.svelte"
  import Container from "./Container.svelte"

  let say = false

	setTimeout(() => {
		say = true
	}, 1000)
</script>


<Container>
	<!-- this component's div -->
	{#if say}
	  <div>Hello!</div>
	{:else}
	  not saying anything yet...
	{/if}

	<!-- this component and others affected by :global -->
	{#each [2,1,0] as faceIndex}
		<Face index={faceIndex}/>
	{/each}

	<!-- shorthand:
		{#each [2,1,0] as index}
			<Face {index}/>
		{/each}
	 -->

</Container>






<style>
  /* affects styling for html in this component */
  div { color: red; }

	/* affects styling globally, for all components in this file? */
  :global(*) { box-sizing: border-box; }
	:global(body, html) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
	}
</style>
