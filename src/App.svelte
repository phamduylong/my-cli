<script lang="ts">
  const commands = ["help", "whoami", "projects", "contact", "clear"] as const;
  import CommandInput from "./lib/components/CommandInput.svelte";
  let command = "";
</script>

<main>
<p><br/>Welcome to my interactive web terminal.</p>
<p><br/>For a list of available commands, type 'help'.</p>
  <CommandInput bind:command={command} />
</main>

<style>
  p {
    position: relative;
    left: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    width: 100%;
    height: 100%;
    padding: 0 10px;
    color: #B89076;
  }
</style>
