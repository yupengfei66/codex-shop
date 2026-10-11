<script setup>
import { promises } from '../data/menu.js'
</script>

<template>
  <section id="top" class="hero shell" aria-labelledby="hero-title">
    <div class="hero-copy">
      <p class="eyebrow"><span class="eyebrow-number">01 /</span> 一顿热饭，也是一点惦记</p>
      <h1 id="hero-title">把日子过暖，<br /><em>把饭吃香。</em></h1>
      <p class="hero-description">
        一碗慢慢炖好的汤，一桌刚出锅的家常菜。<br class="desktop-break" />
        不赶时间，好好吃饭，今天也要照顾好自己。
      </p>
      <div class="hero-actions">
        <a class="button" href="#menu">看看今天吃什么 <span aria-hidden="true">↓</span></a>
        <a class="text-link" href="#story">认识慢慢食堂 <span aria-hidden="true">↗</span></a>
      </div>
      <p class="hours-note"><strong>每天 11:00—21:30</strong><span>热饭热菜，等你回家</span></p>
    </div>

    <div class="hero-art-wrap">
      <span class="hero-side-note" aria-hidden="true">A TABLE SET FOR YOU · 01</span>
      <div class="hero-art" role="img" aria-label="窗边木桌上摆着一碗热汤、时蔬和筷子">
        <svg viewBox="0 0 640 620" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <defs>
            <linearGradient id="room" x1="0" y1="0" x2="1" y2="1">
              <stop stop-color="#ead6b8" />
              <stop offset="1" stop-color="#d59a70" />
            </linearGradient>
            <linearGradient id="bowl" x1="0" y1="0" x2="0" y2="1">
              <stop stop-color="#fffaf0" />
              <stop offset="1" stop-color="#d7b28b" />
            </linearGradient>
            <linearGradient id="soup" x1="0" y1="0" x2="0" y2="1">
              <stop stop-color="#bf633c" />
              <stop offset="1" stop-color="#803c2c" />
            </linearGradient>
            <filter id="soft-shadow" x="-.3" y="-.3" width="1.7" height="1.8">
              <feGaussianBlur in="SourceAlpha" stdDeviation="12" />
              <feOffset dy="11" />
              <feComponentTransfer><feFuncA type="linear" slope=".2" /></feComponentTransfer>
              <feMerge><feMergeNode /><feMergeNode in="SourceGraphic" /></feMerge>
            </filter>
          </defs>
          <rect width="640" height="620" fill="url(#room)" />
          <path d="M0 0h262v293H0z" fill="#f5e9d3" opacity=".45" />
          <path d="M0 276h262M132 0v294" stroke="#fbf0dd" stroke-width="10" opacity=".8" />
          <circle cx="480" cy="128" r="73" fill="#f4d696" opacity=".88" />
          <path d="M0 413c115-42 222-43 323-4s203 42 317 0v211H0z" fill="#986344" />
          <path d="M0 451c140-30 244-12 352 14s184 22 288-8v163H0z" fill="#7e5139" opacity=".72" />

          <g fill="none" stroke="#fff7e7" stroke-linecap="round" opacity=".78">
            <path d="M210 340c-25-31 23-43 0-78s23-43 0-74" stroke-width="8" />
            <path d="M293 323c-20-26 19-38 0-65s20-37 0-64" stroke-width="7" opacity=".7" />
          </g>

          <g filter="url(#soft-shadow)">
            <ellipse cx="346" cy="456" rx="203" ry="61" fill="#523624" opacity=".28" />
            <path d="M179 337c104-33 230-33 334 0l-31 139c-90 53-184 53-273 0z" fill="url(#bowl)" stroke="#fff8eb" stroke-width="8" />
            <ellipse cx="346" cy="340" rx="168" ry="54" fill="#fff8eb" />
            <ellipse cx="346" cy="343" rx="145" ry="39" fill="url(#soup)" />
            <path d="M263 341c23-24 48 20 73-2s46 21 71-1" fill="none" stroke="#e7a45c" stroke-width="9" stroke-linecap="round" />
            <path d="M280 357c20-15 42 14 63 1s43 14 63 0" fill="none" stroke="#f0cf89" stroke-width="7" stroke-linecap="round" />
            <circle cx="294" cy="329" r="17" fill="#edc467" />
            <circle cx="294" cy="329" r="9" fill="#fff6d9" />
            <path d="M359 326c14-25 26 20 41-3 12-19 24 19 37-2" fill="none" stroke="#819764" stroke-width="13" stroke-linecap="round" />
            <circle cx="404" cy="355" r="11" fill="#d9784c" />
          </g>

          <g transform="translate(113 392)">
            <ellipse cy="9" rx="59" ry="25" fill="#f7ead5" />
            <ellipse cy="4" rx="47" ry="16" fill="#a3a36b" />
            <path d="M-31 2c17-31 32 2 44-19S38 4 46-2" fill="none" stroke="#5d7044" stroke-width="12" stroke-linecap="round" />
            <circle cx="-9" cy="-6" r="7" fill="#dda45d" />
          </g>
          <g transform="rotate(-18 535 415)" stroke-linecap="round">
            <path d="M512 294l22 188" stroke="#68442f" stroke-width="10" />
            <path d="M538 289l22 187" stroke="#a87851" stroke-width="8" />
          </g>
          <g fill="#65794b">
            <path d="M73 96c-42-47-64-10-53 11 18 1 36-2 53-11" />
            <path d="M77 98c-10-58 31-57 42-37-6 15-20 28-42 37" />
            <path d="M78 106c-49-19-52 18-34 31 16-5 28-14 34-31" />
          </g>
          <path d="M74 105c13 42 9 72 3 109" fill="none" stroke="#65794b" stroke-width="6" />
          <path d="M633 0v620" stroke="#f6e2c1" stroke-width="2" opacity=".3" />
        </svg>
        <div class="art-sticker"><span aria-hidden="true">☼</span>厨房里，有刚出锅的香气</div>
      </div>
      <span class="hero-caption">一日三餐里的小小认真 <span>— MM / EVERYDAY</span></span>
    </div>

    <div class="promise-row" aria-label="我们的坚持">
      <div v-for="(promise, index) in promises" :key="promise.text" class="promise-item">
        <span class="promise-number">0{{ index + 1 }}</span>
        <span class="promise-icon" aria-hidden="true">{{ promise.icon }}</span>
        <span>{{ promise.text }}</span>
      </div>
    </div>
  </section>
</template>
