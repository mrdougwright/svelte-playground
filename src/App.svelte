<script>
  import Face from './Face.svelte';
  import Container from './Container.svelte';
  import Header from './Header.svelte';
  import Buttons from './Buttons.svelte';
  import story from './story';

  let showHeader = false
	let happyScore = 0
	let storyIndex = 0

	$: smileySays = showMsg(storyIndex)
	$: buttons = story[storyIndex].buttons

	$: if (happyScore > 0 && storyIndex === 3) showHeader = true

	const clickHandler = (e) => {
		storyIndex += 1
		happyScore += e.detail.value
	}
	let name = "Doug"
	let count = 0

	const showMsg = (index) => {
		let msg = story[index]
		if (index === 5) {
			if (happyScore > 0) {
			  return msg.end.nice
			} else if (happyScore < 0) {
				return msg.end.mean
			}
				return msg.end.neutral
		}

		if (index === 6) {
			storyIndex = 0
			happyScore = 0
		}
		return story[storyIndex].smileySays
	}
</script>

<!-- Final Challenge
1. Header appears if user chooses Svelte answer
(HINT: happyScore will be greater than 0 if they answer Svelte)
2. Display final message depending on happyScore
3. Implement the Reset functionality
-->

{#if showHeader}
  <Header />
{/if}

<Container>
  <input type="text" bind:value={name}>
  <h1>{name}, {smileySays}</h1>
  <Face {happyScore} size={storyIndex + 1} />
  <Buttons {buttons} on:click={clickHandler}/>
</Container>


<style>
  h1 {
		text-align: center;
		background: #ff3e00;
		font-size: 2em;
    padding: 0.3em .6em;
	  color: white;
		border-radius: 50px;
	}
	input {
		margin: 1em;
		width: 250px;
		font-family: 'Nunito', sans-serif;
		border: 0;
		outline: 0;
		background: transparent;
		border-bottom: 1px solid black;
		text-align: center;
		font-size: 2em;
    }
    :global(*) {
		box-sizing: border-box;
	}
	:global(body, html) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
	}
</style>