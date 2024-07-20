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
{#each data.monsters as monster (monster.url)}
    <p>{monster.id}: {monster.name} </p>
{/each}

<style>
    h1 {
        color: red;
    }
</style>