<script lang="ts">
  import { interiorPages } from "$lib/config"
  import { page } from "$app/stores"
  import Logo from "$lib/Logo.svelte"
  import BtnArrow from "./BtnArrow.svelte"

  let isActive = false

  function toggleNav() {
    isActive = !isActive
  }

  // add class to header when user scrolls 100px
  let y: any
</script>

<svelte:window bind:scrollY={y} />

<nav id="mainnav" class:active={isActive} class={y >= 100 ? "scroll" : ""}>
  <div class="container top">
    <!-- Logo -->
    <a id="logo" href="/">
      <Logo />
    </a>

    <!-- Nav links -->
    <div class="nav-links-wrapper" class:active={isActive}>
      <ul id="nav-links">
        <li class="nav-link" class:active={$page.url.pathname === "/"}>
          <a href="/" on:click={toggleNav}>home</a>
        </li>
        {#each interiorPages as { name, path }}
          <li class="nav-link" class:active={$page.url.pathname.startsWith(path)}>
            <a href={path} on:click={toggleNav}>{name}</a>
          </li>
        {/each}
      </ul>

      <!-- Nav wrap CTA -->
      <a href="/contact" class="btn" on:click={toggleNav}>get in touch<BtnArrow /></a>
    </div>

    <!-- Toggle -->
    <button id="toggle" aria-label="Toggle" class:active={isActive} on:click={toggleNav}>
      <span class="wrap">
        <span style="--index: 1" />
        <span style="--index: 2" />
        <span style="--index: 3" />
      </span>
    </button>
  </div>
</nav>
