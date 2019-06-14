<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "Kevin Doocey",
      goals: 21,
      position: "Forward"
    },
    {
      name: "Salomon Rondon",
      goals: 45,
      position: "Forward"
    },
    {
      name: "Ayoze Perez",
      goals: 34,
      position: "Forward"
    }
  ];

  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = e => {
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player
        name={player.name}
        goals={player.goals}
        position={player.position}
        on:removeplayer={removePlayer} />
    {/each}
  {/if}
</div>
