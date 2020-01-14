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
  .linkList {
    background-color: #f6f6ef;
    margin: 0;
    padding: 0;
  }
</style>

<ul class="linkList">
  {#each items as item, index}
    <LinkItem {index} {item} />
  {/each}
</ul>
