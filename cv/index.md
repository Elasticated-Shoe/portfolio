---
layout: page
title: CV
permalink: /cv/
---

<link rel="stylesheet" href="/assets/minima-overrides.css">

My CV is included below. This CV uses a template built in react from [cv-templates](https://github.com/Elasticated-Shoe/cv-templates). The content is populated by a seperate, uncommited file.

The build process for this site clones and builds it, so you will also not find the built files in this repo.

<a href="/assets/cv/index.html" target="_blank" rel="noopener">open it in a new tab.</a>

<iframe id="cv-iframe" src="/assets/cv/index.html" style="width:100%; min-height:80vh; border:1px solid #ccc; border-radius:8px; background:#fff; overflow:hidden;" title="CV" loading="lazy" referrerpolicy="no-referrer" scrolling="no"></iframe>

<script>
  function resizeIframeToContent(iframe) {
      iframe.style.height = iframe.contentWindow.document.documentElement.scrollHeight + 'px';
  }
  document.addEventListener('DOMContentLoaded', function() {
    const iframe = document.getElementById('cv-iframe');
    iframe.addEventListener('load', function() {
      resizeIframeToContent(iframe);
      // Fix for Chrome: re-apply resize after a short delay
      setTimeout(function() {
        resizeIframeToContent(iframe);
      }, 100);
      try {
        const links = iframe.contentDocument.querySelectorAll('a[href]');
        links.forEach(link => {
          link.addEventListener('click', function(e) {
            e.preventDefault();
            window.location.href = link.href;
          });
        });
      } catch (err) {
        
      }
    });
  });
</script>
