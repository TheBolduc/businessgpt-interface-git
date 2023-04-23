<!-- src/routes/chatbots.svelte -->
<svelte:head>
	<title>Chatbots</title>
</svelte:head>


<script context="module">
    // Update the fetch URL with your chatbot data API or use the same JSONPlaceholder API
    export const load = async ({ fetch }) => {
        const res = await fetch("https://jsonplaceholder.typicode.com/posts");
        const chatbots = await res.json();
        return {
            props: {
                chatbots,
            }
        }
    }
 
</script>

<script>
    export let chatbots; // update the variable name
</script>

<div class="container">
    <h1>My Chatbots</h1> 

    <div class="chatbots">
        {#each chatbots as chatbot} <!-- Update the variable name -->
        <div class="chatbot">
            <h2>{chatbot.title.substring(0, 20)}</h2>
            <p>{chatbot.body.substring(0, 80)}</p>
            <p class="readmore"><a style=" color: rgb(10, 10, 139);" href={`/chatbots/${chatbot.id}`}>View Chatbot</a></p>
        </div> 
        {/each}
    </div>
</div>


<style>
    .container {
        max-width: 800px;
        margin: 50px auto;
    }
    .blogposts {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

    .post {
        border: 1px solid #ddd;
        padding: 10px;
        box-shadow: 0 0 10px #eee;
    }

    h2 {
        margin: 0;
    }

    .readmore {
        color: rgb(10, 10, 139);
        text-align: right;
        margin: 20px 0 0 0;
    }

    .readmore:hover {
        color: green;
    }
</style>