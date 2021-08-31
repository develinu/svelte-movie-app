<script>
  import { fade } from 'svelte/transition'
  import Router, { location } from 'svelte-spa-router'
  import routes from '~/routes'
  import Header from '~/components/Header.svelte'
  import Footer from '~/components/Footer.svelte'
</script>

<Header />
{#key $location}
  <div
    in:fade>
    <Router {routes} restoreScrollState />
  </div>
{/key}
<Footer />
<style lang="scss">

</style>