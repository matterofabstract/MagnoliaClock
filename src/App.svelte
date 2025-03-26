<script>
  import Landscape from './lib/Landscape.svelte';
  import Portrait from './lib/Portrait.svelte';

  const checkOrientation = () => {
    if (window.screen?.orientation?.type) {
      return window.screen.orientation.type.includes('landscape');
    }
    return window.innerWidth > window.innerHeight;
  };

  let isLandscape = checkOrientation();

  $: {
    const color = isLandscape ? 'black' : '#f3f4f6';
    document.documentElement.style.backgroundColor = color;

    // Update theme-color meta tag
    let themeColorMeta = document.querySelector('meta[name="theme-color"]');
    if (themeColorMeta) {
      themeColorMeta.setAttribute('content', color);
    }

    // Update apple-mobile-web-app-status-bar-style
    let statusBarMeta = document.querySelector('meta[name="apple-mobile-web-app-status-bar-style"]');
    if (statusBarMeta) {
      statusBarMeta.setAttribute('content', isLandscape ? 'black' : 'black-translucent');
    }
  }
</script>

<svelte:window
  on:resize={() => isLandscape = checkOrientation()}
  on:orientationchange={() => isLandscape = checkOrientation()}
/>

{#if isLandscape}
  <Landscape />
{:else}
  <Portrait />
{/if}
