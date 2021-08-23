<script>
  import { link } from 'svelte-spa-router'
  import active from 'svelte-spa-router/active'
  import Logo from '~/components/Logo.svelte'

  const menus = [
    {
      href: '/',
      name: 'Search'
    },
    {
      href: '/movie/tt4520988',
      name: 'Movie',
      path: '/movie/*'
    },
    {
      href: '/about',
      name: 'About',
      path: '/about'
    }
  ]
</script>

<header>
  <Logo />
  <nav>
    <ul>
      {#each menus as {href, name, path} (name)}
        <li>
          <a 
            use:link 
            use:active={path}
            {href}>
            {name}
          </a>
        </li>
      {/each}
    </ul>
  </nav>  
</header>

<style lang="scss">
  header :global(a.active) {
    color: red;    
  }
</style>