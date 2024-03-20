<script setup>
useSeoMeta({
  ogTitle: "Home",
  ogDescription: "TurboAnime - A streaming service for weebo...",
  ogUrl: useRoute().fullPath,
  twitterTitle: "Home",
  twitterDescription: "TurboAnime - A streaming service for weebo...",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  title: "Home",
});
</script>

   <style>
    .intro-app{ position: relative; font-size: 14px; margin: 2rem auto; max-width: 700px; overflow: hidden; background: rgb(69,12,14); background: linear-gradient(148deg, rgba(69,12,14,1) 0%, rgba(163,23,28,1) 100%);}
    .intro-app::before{ content: ""; position: absolute; top: 10px; left: 10px; right: 10px; bottom: 10px; border: 1px solid rgba(255,255,255,.2); z-index: 1;}
    .intro-app .ina-flex{ display: flex; align-items: stretch; flex-direction: row-reverse; position: relative; padding: 2rem; z-index: 3;}
    .intro-app .ina-flex .ina-screen{ width: 240px; flex-shrink: 0; position: absolute; right: 30px; top: 20px; animation: app-screen 1s infinite linear;}
    @keyframes app-screen {
        0% { transform: scale(1.05);}
        50% { transform: scale(1);}
        100% { transform: scale(1.05);}
    }
    .intro-app .ina-flex .ina-screen img{ width: 100%;}
    .intro-app .ina-flex .ina-content{ flex-grow: 1;}
    .ina-head-lg{ font-size: 1.6em; line-height: 1.4; color: #fff; font-weight: 600; margin-bottom: .5rem;}
    .ina-head-md{ font-size: 1em; line-height: 1.4; color: #fff; font-weight: 500; margin-bottom: 1.5rem; opacity: .8;}
    .is-fea{ padding: 1rem 0 3rem;}
    .is-fea .ina-ul{ padding: 0; margin: 0; list-style: none;}
    .is-fea .ina-ul li{ position: relative; padding: .5rem 0 .5rem 1.2rem; font-size: 15px;}
    .is-fea .ina-ul li:before{ content: ""; width: 6px; height: 6px; border-radius: 50%; background-color: #fff; display: block; position: absolute; top: calc(50% - 3px); left: 0;}
    .ina-buttons{ display: flex; flex-direction: column; gap: 1rem; max-width: 500px;}
    .ina-buttons .btn{ padding: .75rem 1rem; border-radius: .4rem; font-size: 14px; font-weight: 500; max-width: 180px; background-color: #fff; color: #111 !important;}
    @media screen and (max-width: 740px){
        .intro-app{ border-radius: 0;}
        .intro-app .ina-flex{ padding: 1.5rem; padding-right: 160px;}
        .intro-app .ina-flex .ina-screen{ width: 160px; right: -10px; top: 10px;}
        .ina-head-lg{ font-size: 1.2em;}
        .ina-head-md{ font-size: .9em; margin-bottom: 1rem;}
        .ina-buttons .btn{ padding: 0; background-color: transparent; color: #fff !important; width: auto !important;}
        .ina-buttons .btn > div{ justify-content: flex-start !important;}
    }
</style>
<div class="intro-app" style="display: none">
    <div class="ina-flex">
        <div class="ina-screen">
            <img src="/images/download-apk.webp">
        </div>
        <div class="ina-content">
            <h1 class="ina-head-lg">BEST Free Anime App</h1>
            <h2 class="ina-head-md">Watch all Anime in HD on your Android devices</h2>
            <div class="ina-buttons">
                <a class="btn" href="/app-download">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="mr-3">Download Now</span>
                        <i class="fas fa-angle-right"></i>
                    </div>
                </a>
            </div>
        </div>
    </div>
</div>
<script>
  if (navigator.userAgent.match(/Android/i)) {
    document.querySelector('.intro-app').style.display = "block"
  }
</script>

<template>
  <PgCompsLandingPage />
</template> 

<style></style>
