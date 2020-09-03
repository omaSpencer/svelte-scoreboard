<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let player = {
    name: '',
    points: 0,
  };

  const onSubmit = (e) => {
    e.preventDefault();

    dispatch('addplayer', player);

    player = {
      name: '',
      points: 0,
    };
  };
</script>

<style>
  form {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  input[type='submit'] {
    font-size: 1.2rem;
    padding: 0.75rem 0.5rem;
    border-radius: 4px;
    background-color: #444b6e;
    color: #fff;
  }

  @media screen and (max-width: 500px) {
    form {
      flex-direction: column;
    }

    form > * {
      width: 100%;
      text-align: center;
      margin: 1.125rem 0 0;
    }
  }
</style>

<form on:submit={onSubmit}>
  <input type="text" placeholder="Player Name" bind:value={player.name} />
  <input type="text" placeholder="Player Points" bind:value={player.points} />
  <input type="submit" value="Add Player" />
</form>
