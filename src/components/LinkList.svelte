<script>
  import LinkItem from "./LinkItem.svelte";

  import { getClient, query } from "svelte-apollo";
  import { gql } from "apollo-boost";

  const client = getClient();
  const FEED_QUERY = gql`
    query FeedQuery($first: Int, $skip: Int, $orderBy: LinkOrderByInput) {
      feed(first: $first, skip: $skip, orderBy: $orderBy) {
        links {
          id
          createdAt
          url
          description
          postedBy {
            id
            name
          }
          votes {
            id
            user {
              id
            }
          }
        }
        count
      }
    }
  `;

  const _getQueryVariables = () => {
    const isNewPage = true;
    const pageParam = 1;

    const skip = 0;
    const first = 100;
    const orderBy = "createdAt_DESC";
    return { first, skip, orderBy };
  };

  const links = query(client, {
    query: FEED_QUERY,
    variables: _getQueryVariables()
  });
  console.log("links", links);
</script>

<style>
  .linkList {
    background-color: #f6f6ef;
    margin: 0;
    padding: 0;
  }
</style>

{#await $links}
  Loading...
{:then result}
  <ul class="linkList">
    {#each result.data.feed.links as link, index}
      <LinkItem {index} {link} />
    {/each}
  </ul>
{:catch error}
  Error: {error}
{/await}
