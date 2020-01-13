<script>
  import LinkItem from "./LinkItem.svelte";

  let items = [
    {
      title: "test",
      url: "abc"
    },
    {
      title: "teste1",
      url: "cde"
    }
  ];
</script>

<style>
  /* your styles go here */
</style>

<ul>
  {#each items as item}
    <LinkItem {item} />
  {/each}
</ul>
