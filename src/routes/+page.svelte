<script>
  // components

  // stores
  import { URL, companyName, industry, cityAndState, interiorPages, services } from "$lib/config"
  import { page } from "$app/stores"
  // styles
  import "$styles/home.less"
  import BtnArrow from "$lib/components/BtnArrow.svelte"

  // logic
  const thisPage = interiorPages.find((p) => p.path === $page.route.id)

  // Email CTA
  let ctaEmail = ""

  function submitCTAForm() {
    alert(ctaEmail)

    // clear field
    ctaEmail = ""
  }

  $: console.log(ctaEmail)
</script>

<svelte:head>
  <!-- preload hero imgs -->
  <!-- <link rel="preload" as="image" href="/heromobile.webp" />
  <link rel="preload" as="image" href="/hero.webp" /> -->

  <meta property="og:type" content="website" />
  <meta property="og:site_name" content="Business Name" />
  <meta property="og:title" content="" />
  <meta property="og:url" content={URL} />
  <meta name="description" content={thisPage?.metaDescription} />
  <meta property="og:description" content={thisPage?.metaDescription} />
  <link rel="canonical" href={URL} />
  <meta property="og:image" content="" />
  <meta property="og:image:secure_url" content="" />
  <meta property="og:url" content="" />
  <!-- <meta property="article:published_time" content="" />
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content="" />
  <meta name="twitter:description" content="" />
  <meta name="twitter:site" content="" />
  <meta name="twitter:creator" content="" />
  <meta name="twitter:image" content="" />
  <meta name="twitter:label1" content="" />
  <meta name="twitter:data1" content="" />
  <meta name="twitter:label2" content="" />
  <meta name="twitter:data2" content="" /> -->

  <title>{companyName} | {industry} | {cityAndState}</title>
</svelte:head>

<section id="landing">
  <div class="content">
    <h1>small business web development & design</h1>
    <p>
      We are a Tulsa Web Design agency that provides custom-coded, professionally designed websites
      that deliver premium results. No WordPress or Page-builders.
    </p>

    <!-- <a href="/" class="btn"
      >get in touch
      <BtnArrow />
    </a> -->

    <!-- 1. Enter email 2. Show modal with email filled + add. fields 3. Submit-->
    <form class="cta-email" on:submit|preventDefault={submitCTAForm}>
      <input
        id="cta-email"
        class:active={ctaEmail.length > 0}
        type="text"
        name="Email for Modal"
        placeholder="enter your email"
        required
        bind:value={ctaEmail} />
      <label for="cta-email" class="screenreader">enter your email</label>
      <button>get in touch <BtnArrow /></button>
    </form>
  </div>

  <div class="video-wrapper">
    <video id="herovid" preload="none" autoplay loop muted playsinline poster="/video/poster.jpg">
      <source type="video/mp4" src="/video/hero-video.mp4" />
    </video>
  </div>
</section>
