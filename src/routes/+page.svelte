<script lang="ts">
    import {hello} from "./hello";
    import type {PageData} from "./$types";
    import type {IndexMonster} from "./+page";
    import { generations } from "./generations";

    const greetingObject = {
        greeting: "Test",
        name: "World"
    };

    export let data: PageData;

    let monsterId: string;
    $: monster = data.monsters.find((monster) => monster.id === monsterId)
    const monsterClick = (monster: IndexMonster) => {
        monsterId = monster.id;
    }
</script>
<h2>{monster?.name}</h2>
<h1>Welcome to {hello} {greetingObject.name}</h1>

<div class="generations">
    {#each generations as generation (generation.id)}
      <div class="generation">{generation.main_region}</div>
    {/each}
</div>

<div class="monsters">
    {#each data.monsters as monster (monster.url)}
        <div class="monster" on:click={() => monsterClick(monster)}>
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

    .generations {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
    }

    .generation {
        margin: 10px;
        padding: 5px 10px;
        border: 1px solid black;
        background-color: #eaeaea;
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