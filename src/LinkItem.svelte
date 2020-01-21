<script>
  export let link;
  export let index;
</script>

<style>
  .itemWrapper {
    list-style-type: none;
    margin: 0 0.5rem;
    color: #828282;
    height: 3rem;
  }
</style>

<li class="itemWrapper">{index}. {link.description} ({link.url})</li>
