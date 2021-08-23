<footer>
  <div>
    <a href="https://github.com/develinu/svelte-movie-app">
      GitHub Repo.
    </a>
  </div>
  <div>
    <a href="https://devinu.notion.site/8f5cdaadde1547ca82a4c13d97a76d47">
      @{new Date().getFullYear()}
      Devinu
    </a>
  </div>
</footer>

<style lang="scss">
  footer {
    padding: 70px;
    text-align: center;
    a {
      color: $color--white-10;
      text-decoration: none;
      &:hover {
        text-decoration: underline;
      }
    }
  }
</style>