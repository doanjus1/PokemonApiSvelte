<script lang="ts">
    import type { IndexMonster } from "./+page";


  export let monster: IndexMonster;
  export let updateSearchParams: (key: string, value: string) => void;
  export let isInteractive: boolean = false;
</script>

<div class="monster">
  <div on:click={() => isInteractive ? updateSearchParams('monsterId', monster.id) : () => {}}>
    <div class="monster-container">
      <img src={monster.image} alt={monster.name} />
      {monster.name}
    </div>
    <div class="monster-id">
      {monster.id}
    </div>
  </div>
</div>

<style>
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