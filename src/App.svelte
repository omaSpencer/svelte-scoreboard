<script>
  import Navbar from './Navbar.svelte';
  import Player from './Player.svelte';
  import AddPlayer from './AddPlayer.svelte';

  let players = [
    {
      name: 'John Doe',
      points: 23,
    },
    {
      name: 'Sam Smith',
      points: 56,
    },
    {
      name: 'Sara Wilson',
      points: 12,
    },
  ];

  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = (e) => {
    players = players.filter((player) => player.name !== e.detail);
  };
</script>

<style>
  main {
    background-color: #9ab87a;
    color: #fff;
    min-height: 100vh;
  }
</style>

<main>
  <Navbar />
  <div class="container">
    <AddPlayer on:addplayer={addPlayer} />
    {#if players.length === 0}
      <p>No Players</p>
    {:else}
      {#each players as player}
        <Player
          name={player.name}
          points={player.points}
          on:removeplayer={removePlayer} />
      {/each}
    {/if}
  </div>
</main>
