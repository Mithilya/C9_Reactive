<script>
  let launches = [];

  async function fetchLaunches() {
    const response = await fetch('https://api.spacexdata.com/v4/launches/upcoming');
    const data = await response.json();
    launches = data;
  }

  fetchLaunches();
</script>

<h1>Upcoming SpaceX Launches</h1>

{#if launches.length > 0}
  <ul>
    {#each launches as launch}
      <li class="launch-item">
        <strong>{launch.name}</strong> - {launch.date_utc}
      </li>
    {/each}
  </ul>
{:else}
  <p>Loading...</p>
{/if}

<style>
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
</style>