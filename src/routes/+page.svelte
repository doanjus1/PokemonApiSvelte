<script lang="ts">
    import {hello} from "./hello";
    import type {PageData} from "./$types";

    const greetingObject = {
        greeting: "Test",
        name: "World"
    };

    export let data: PageData;
</script>

<h1>Welcome to {hello} {greetingObject.name}</h1>
<div class="monsters">
    {#each data.monsters as monster (monster.url)}
        <div class="monster">
            <div class=monster-container>
                <img src={monster.image} alt={monster.name}/>
                {monster.name}
            </div>
            <div class='monster-id'>
                {monster.id}
            </div>
        </div>
    {/each}
</div>

<style>
    h1 {
        color: red;
    }

    .monsters {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
    }

    .monster-id{
        position: absolute;
        top: 0;
        left: 0;
        padding-left: 5px;
        font-size: 0.8em;
    }
    .monster {
        width: 100px;
        margin: 10px;
        padding: 10px;
        position: relative;
        background-color: #eee;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }

    .monster:hover {
        background-color: #ddd;
    }
    .monster-container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>