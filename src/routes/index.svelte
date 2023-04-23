<!-- src/routes/index.svelte -->
<svelte:head>
	<title>David Adeneye</title>
</svelte:head>

<script>
import { onMount } from "svelte";
import { OpenAI }  from "../lib/openai";

  const chatbots = [
    { id: 1, name: "Chatbot 1" },
    { id: 2, name: "Chatbot 2" },
    { id: 3, name: "Chatbot 3" },
    { id: 4, name: "Chatbot 4" },
    { id: 5, name: "Chatbot 5" },
    { id: 6, name: "Chatbot 6" },
  ];
</script>

<div class="container">
	<div class="info">
		<div class="animate-background">
		  <div class="container info-container">
			<div class="info-text">
			  <h1>
				<p class="animate-text-1">School-taught Computer Scientist,</p>
				<p class="text-2">Self-taught Software Engineer</p>
			  </h1>
			</div>
			<h2 class="subtitle">
			  On a mission to help SMEs across the globe do businesses seamlessly and digitally.
			</h2>
			<div style="color:black" class="scroll-button animate-scroll" tabindex="0">
			  <a href="/about">See More About Me</a><div class="arrow">→</div>
			</div>
		  </div>
		</div>
	</div>
  
  <div id="app">
    <form on:submit|preventDefault={handleSubmit}>
      <label for="user-input">Ask GPT-3</label>
      <input
        id="user-input"
        type="text"
        bind:value={userInput}
        placeholder="Type your question"
        required
      />
      <button type="submit">Submit</button>
    </form>
    {#if isLoading}
      <p>Loading...</p>
    {:else if response}
      <p>{response.choices[0].text.trim()}</p>
    {/if}
  </div>
  
</div>

<h2>Select a Chatbot:</h2>

	<ul>
	  {#each chatbots as chatbot}
	    <li>
	      <a href="/chatbots/{chatbot.id}">{chatbot.name}</a>
	    </li>
	  {/each}
	</ul>
</div>

<div class="background-div"></div>


<style>
    .info {
        text-align: center;
        position: relative;
    }        

    .info-container {
        height: 100%;
        display:flex;
        flex-direction: column;
        justify-content: center;
        text-align: left;
        align-items: start;
    }

    .container {
		    max-width: 1400px;
        margin: 190px 0 0 2rem;
    }

    .info h1 {
        font-size: 4rem;
        margin: 0;
    }

    .info h1 p {
        position: relative;
        font: inherit;
        margin: 0;
		text-align: left;
        line-height: 130%;
        width: fit-content;
        font-weight: 800;
        letter-spacing: -0.03em;
    }

    .info h2 {
        max-width: 65ch;
        font-weight: 200;
        margin-top: 0.50rem;
    }

	.background-div {
		background-color: var(--background);
    	width: 100%;
		height: 56vh;
		margin: -155px auto;
	}
    
   
    .info .info-text {
        position: relative;
    }

	.scroll-button { 
		display: flex;
		border: none;
		outline: none;
		cursor: pointer;
	}

  	.scroll-button .arrow {
  		margin-left: 0.50rem;
	}

</style>