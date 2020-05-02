<script>
  import Face from "./Face.svelte"

  let say = "hi"
	setTimeout(() => {
		say = 'bye'
	}, 1000)
</script>

<style>
  /* affects styling for html in this component */
  div { color: red }

	/* affects styling globally, for all components in this file? */
	:global(div) {
		background: #cbdbf4;
	}
</style>

<!-- this component's div -->
<div> Say: {say} </div>

<!-- this component and others affected by :global -->
<Face size="4"/>
<Face size="10"/>
<Face />
