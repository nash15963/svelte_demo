<!-- @format -->
<script lang="ts">
  import Status from "./lib/Status.svelte";
  import Time from "./lib/Time.svelte";

  let name = "";
  let email = "";
  let message = "";
  let form;

  const handleSubmit = () => {
    console.log(name, email, message);
    alert("Form submitted: " + JSON.stringify({ name, email, message }));
  };

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

  <p>some content</p>
  <button on:click={submitForm}>Submit</button>
  <Status />
  <Time />
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
</style>
