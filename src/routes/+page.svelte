<script>
	// components

	// stores
	import { URL, companyName, industry, cityAndState, interiorPages, services } from '$lib/config';
	import { page } from '$app/stores';
	// styles
	import BtnArrow from '$lib/components/BtnArrow.svelte';
	import { onMount } from 'svelte';

	// logic
	const thisPage = interiorPages.find((p) => p.path === $page.route.id);

	// Email CTA
	let ctaEmail = '';

	function submitCTAForm() {
		alert(ctaEmail);

		// clear field
		ctaEmail = '';
	}
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
			We are a Tulsa Web Design agency that provides custom-coded, professionally designed websites that deliver premium
			results. No WordPress or Page-builders.
		</p>

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
		<video id="herovid" preload="none" autoplay loop muted playsinline poster="">
			<source type="video/mp4" src="/video/hero-video.mp4" />
		</video>
	</div>
</section>

<!----                      ---->
<!----    Divider      ---->
<!----                      ---->

<section id="services">
	<h2 class="title">what we do</h2>
	<p class="section-description">
		Rivas Web Designs provides advanced digital marketing solutions with custom web development and design. Our
		professionally crafted websites set you apart from the competition, boosting revenue. Say goodbye to generic templates
		and elevate your business with a unique, tailored online presence.
	</p>

	<div class="card">
		<h3 class="title">website design</h3>
		<p>
			Our web designs are original developed with thorough research and expertise to deliver the best user experience for
			your customers.
		</p>
		<a href="/" class="btn">
			get in touch
			<BtnArrow />
		</a>
	</div>

	<div class="card">
		<h3 class="title">website development</h3>
		<p>
			We don’t use WordPress or page-builders. Our websites are hand-coded from scratch in order to achieve the best
			performance and flexibility.
		</p>
		<a href="/" class="btn">
			get in touch
			<BtnArrow />
		</a>
	</div>

	<div class="card">
		<h3 class="title">maintenance & support</h3>
		<p>
			No worrying about finding time to update your website. We take care of all website maintenance and edits the same day.
		</p>
		<a href="/" class="btn">
			get in touch
			<BtnArrow />
		</a>
	</div>
</section>
