---
layout: "single"
permalink: "/photos/"
redirect_from:
  - /gallery/
title: "Photos"
classes: "wide"
---
<div class="lang-content lang-en" markdown="1">
## Google Photos Album

Browse the shared Google Photos album curated for Dr. Ponnavaikko directly below.

<p><a class="btn" href="https://photos.app.goo.gl/d334h9MpQRofwpY57" target="_blank" rel="noopener">Open in Google Photos</a></p>
</div>

{% assign photos = site.data.manifest.photos %}
{% if photos and photos.size > 0 %}
<div class="photo-album-grid" data-gallery>
  {% for photo in photos %}
  <figure class="photo-album-grid__item">
    <button
      type="button"
      class="photo-album-grid__trigger"
      data-full="{{ photo.src }}"
      data-alt="{{ photo.alt | escape }}"
    >
      <img
        src="{{ photo.thumb }}"
        data-full-src="{{ photo.src }}"
        alt="{{ photo.alt | escape }}"
        loading="lazy"
        decoding="async"
      />
    </button>
  </figure>
  {% endfor %}
</div>
{% endif %}
<div class="photo-lightbox" data-gallery-lightbox hidden>
  <div class="photo-lightbox__backdrop" data-gallery-dismiss></div>
  <figure class="photo-lightbox__content">
    <img src="" alt="" />
    <figcaption></figcaption>
    <button type="button" class="photo-lightbox__close" data-gallery-dismiss aria-label="Close photo">&times;</button>
  </figure>
</div>
<script>
  document.addEventListener('DOMContentLoaded', () => {
    const gallery = document.querySelector('[data-gallery]');
    const lightbox = document.querySelector('[data-gallery-lightbox]');
    if (!gallery || !lightbox) return;

    const image = lightbox.querySelector('img');
    const caption = lightbox.querySelector('figcaption');
    const dismiss = () => {
      lightbox.classList.remove('is-visible');
      lightbox.setAttribute('hidden', 'hidden');
      image.removeAttribute('src');
      image.removeAttribute('alt');
      caption.textContent = '';
    };

    lightbox.querySelectorAll('[data-gallery-dismiss]').forEach((trigger) => {
      trigger.addEventListener('click', dismiss);
    });

    document.addEventListener('keydown', (event) => {
      if (event.key === 'Escape' && lightbox.classList.contains('is-visible')) {
        dismiss();
      }
    });

    gallery.querySelectorAll('[data-full]').forEach((trigger) => {
      trigger.addEventListener('click', () => {
        const fullSrc = trigger.dataset.full;
        const altText = trigger.dataset.alt || 'Album photo';
        if (!fullSrc) return;
        image.src = fullSrc;
        image.alt = altText;
        caption.textContent = altText;
        lightbox.removeAttribute('hidden');
        lightbox.classList.add('is-visible');
      });
    });
  });
</script>

<div class="lang-content lang-ta" markdown="1">
### Google புகைப்படத் தொகுப்பு

இந்தப் பக்கம் Dr. பண்ணவைக்கோ அவர்களுக்காக பகிரப்பட்ட Google Photos album-ஐ நேரடியாகக் காட்டுகிறது.

<p><a class="btn" href="https://photos.app.goo.gl/d334h9MpQRofwpY57" target="_blank" rel="noopener">Google Photos-ல் முழு தொகுப்பைக் காண</a></p>
</div>
