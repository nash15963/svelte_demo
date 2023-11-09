<!-- @format -->
<script lang="ts">
  type TStatus = "idle" | "pending" | "success" | "error";
  let status: TStatus = "idle";
  const statusList: TStatus[] = ["idle", "pending", "success", "error"];
</script>

<div class="status_container">
  {#each statusList as item}
    <button
      class="status-button"
      class:idle={status === "idle" && item === "idle"}
      class:pending={status === "pending" && item === "pending"}
      class:success={status === "success" && item === "success"}
      class:error={status === "error" && item === "error"}
      on:click={() => (status = item)}
    >
      {item}
    </button>
  {/each}

  <p>status: <span>{status}</span></p>
</div>

<style>
  .status_container {
    margin: 20px auto;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-items: center;
    width: 300px;
    height: 200px;
    border: 1px solid rgb(222, 211, 211);
  }

  .status_container span {
    color: rgb(195, 60, 60);
  }
  .status_container p {
    width: 120px;
    margin: 5px auto;
  }
  .status-button {
    padding: 8px 16px;
    margin: 4px;
    border: none;
    color: white;
    cursor: pointer;
  }

  .idle {
    background-color: grey;
  }

  .pending {
    background-color: yellow;
    color: black;
  }

  .success {
    background-color: green;
  }

  .error {
    background-color: red;
  }
</style>
