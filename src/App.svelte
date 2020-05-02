<script>
  import Face from "./Face.svelte"
  import Container from "./Container.svelte"

  let say = "hi"
	setTimeout(() => {
		say = 'bye'
	}, 1000)
</script>


<Container>
	<!-- this component's div -->
	<div> Say: {say} </div>

	<!-- this component and others affected by :global -->
	<Face index={0} size="10"/>
	<Face index={1} size="4"/>
	<Face index={2}/>
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
