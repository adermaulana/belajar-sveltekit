
<script>
    import Nav from "../library/nav.svelte";
    import Title from "../library/title.svelte";
    import Background from "../library/background.svelte";
    import { onMount } from "svelte";

    const apiURL = "https://jsonplaceholder.typicode.com/posts";
    let data = [];

    onMount(async function() {
        const response = await fetch(apiURL);
        data = await response.json();
    });

</script>


<Nav />
<Title />
<Background />
<div class="guides">
    <ul>
        <li><a href="/guides">Guide 1</a></li>
        <li><a href="/">Back To Home</a></li>
    </ul>
</div>


<div class="item">
    {#each data as item}
    <table border="1">
        <tr>
            <td>{item.id}</td>
            <td>{item.title}</td>
            <td>{item.body}</td>
        </tr>


    </table>
        
    {/each}
</div>

<style>
    .item {
        display: flexbox;
        text-align: justify;
    }
</style>
