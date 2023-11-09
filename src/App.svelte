<!-- @format -->
<script lang="ts">
  type TStatus = "idle" | "pending" | "success" | "error";

  let name = "";
  let email = "";
  let message = "";
  let form;

  let status: TStatus = "idle";
  const statusList: TStatus[] = ["idle", "pending", "success", "error"];

  const handleSubmit = () => {
    console.log(name, email, message);
    alert("Form submitted: " + JSON.stringify({ name, email, message }));
  };

  // 这个函数会在外部按钮被点击时调用
  const submitForm = () => {
    handleSubmit();
  };
</script>

<main>
  <form bind:this={form} on:submit|preventDefault={handleSubmit}>
    <div class="container">
      <input type="text" name="name" placeholder="Name" bind:value={name} />
      <input type="text" name="email" placeholder="Email" bind:value={email} />
      <input
        type="text"
        name="message"
        placeholder="Message"
        bind:value={message}
      />
    </div>
  </form>
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
  <p>some content</p>

  <button on:click={submitForm}>Submit</button>
</main>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 300px;
    height: 200px;
    border: 1px solid rgb(222, 211, 211);
  }
  .container input {
    margin: 5px auto;
    width: 80%;
  }

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

  /* 定义状态的CSS类 */
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
