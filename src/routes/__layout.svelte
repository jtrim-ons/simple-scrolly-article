<script>
  import { page } from '$app/stores';
  import "../app.css";
  import AnalyticsBanner from "$lib/layout/AnalyticsBanner.svelte";

  // GOOGLE ANALYTICS
  // Settings for page analytics. Values must be shared with <AnalyticsBanner> component
  const analyticsId = "GTM-MBCBVQS";
  const analyticsProps = {
    "contentTitle": "Story of the Census", // Insert the title of the product here
    "releaseDate": "20220620",
    "contentType": "scrollytelling", // Optional: eg. scrollytelling, exploratory, edutainment?
    "outputSeries": "historyofcensus1801to2021" // Should match the slug for the release on CMS
  };
  let gtag;
</script>

<svelte:head>
    <meta property="og:title" content="Story of the Census" />
    <meta property="og:type" content="website" />
    <meta property="og:url" content="https://www.ons.gov.uk/visualisations/storyofthecensus" />
    <meta property="og:image" content="https://www.ons.gov.uk/visualisations/storyofthecensus/pngs/Story_OG.png" />
    <meta property="og:description" content="An article about the history of the census in England and Wales over 220 years, from the first census in 1801 to 2021 and the future of population statistics." />
    <meta name="description" content="An article about the history of the census in England and Wales over 220 years, from the first census in 1801 to 2021 and the future of population statistics." />
    <title>Story of the Census</title>
    <link rel='icon' type='image/x-icon' href='/favicon.ico' />
</svelte:head>

<AnalyticsBanner {analyticsId} {analyticsProps} {page} bind:gtag/>
<slot/>
