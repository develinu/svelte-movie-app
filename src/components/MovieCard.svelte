<script>
  import { link } from 'svelte-spa-router'
  import Loader from '~/components/Loader.svelte'

  export let movie

  let imageLoading = true

  if (movie.Poster === 'N/A') {
    imageLoading = false
  } else {
    const img = document.createElement('img')
    img.src = movie.Poster
    img.addEventListener('load', () => {
      imageLoading = false
    })
  }
</script>

<a 
  use:link
  href={`/movie/${movie.imdbID}`}
  class="movie">
  {#if imageLoading}
    <Loader 
      scale=".5"
      absolute />
  {/if}
  <div 
    class="poster"
    style="background-image: url({movie.Poster});">
    {#if movie.Poster === 'N/A'}
      OMDbAPI<br />
      N/A
    {/if}
  </div>
  <div class="info">
    <div 
      class="poster"
      style="background-image: url({movie.Poster});">
    </div>
    <div class="year">{movie.Year}</div>
    <div class="title">{movie.Title}</div>
  </div>
</a>

<style lang="scss">
  .movie {
    display: block;
    position: relative;
    width: 200px;
    height: 300px;
    margin: 10px;
    border-radius: 6px;
    text-decoration: none;
    overflow: hidden;
    cursor: pointer;

    &:hover {
      &::after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border: 4px solid $color--primary;
        box-sizing: border-box;
      }
    }
    
    .poster {
      width: 100%;
      height: 100%;
      background-color: $color--area;
      background-position: center;
      background-size: cover;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: "Oswald", sans-serif;
      color: $color--white-5;
      font-size: 20px;
      text-align: center;
    }

    .info {
      width: 100%;
      height: 66px;
      padding: 14px;
      box-sizing: border-box;
      overflow: hidden;
      position: absolute;
      bottom: 0;
      left: 0;

      .poster {
        position: absolute;
        z-index: 0;
        bottom: 0;
        left: 0;
        transform: scale(2);
        filter: blur(5px);
        
        &::after {
          content: "";
          background-color: $color--black-50;
          position: absolute;
          top: 0;
          left: 0;
          width: 200%;
          height: 200%;
        }
      }

      .year {
        position: relative;
        color: $color--primary;
        font-size: 12px;
      }

      .title {
        position: relative;
        color: $color--white;
        font-size: 15px;
        font-family: "Oswald" sans-serif;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }
</style>