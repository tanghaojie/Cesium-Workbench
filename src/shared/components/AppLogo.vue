<template>
  <span
    class="cyber-logo"
    :class="[`cyber-logo--${tone}`, { 'cyber-logo--icon-only': iconOnly }]"
    :aria-label="iconOnly ? platformConfig.fullName : undefined"
  >
    <svg
      class="cyber-logo__mark"
      viewBox="0 0 200 200"
      fill="none"
      role="img"
      :aria-hidden="iconOnly ? undefined : true"
    >
      <title v-if="iconOnly">{{ platformConfig.fullName }}</title>
      <defs>
        <radialGradient :id="ids.bg" cx="50%" cy="45%" r="70%">
          <stop offset="0%" stop-color="#102030" />
          <stop offset="58%" stop-color="#070D16" />
          <stop offset="100%" stop-color="#03060B" />
        </radialGradient>
        <radialGradient :id="ids.aura" cx="50%" cy="50%" r="58%">
          <stop offset="0%" stop-color="#338AAF" stop-opacity="0.42" />
          <stop offset="62%" stop-color="#338AAF" stop-opacity="0.10" />
          <stop offset="100%" stop-color="#338AAF" stop-opacity="0" />
        </radialGradient>
        <linearGradient
          :id="ids.rim"
          x1="0"
          y1="0"
          x2="200"
          y2="200"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0%" stop-color="#67C7EB" stop-opacity="0.45" />
          <stop offset="50%" stop-color="#338AAF" stop-opacity="0.24" />
          <stop offset="100%" stop-color="#E5B66A" stop-opacity="0.36" />
        </linearGradient>
        <radialGradient :id="ids.sphere" cx="38%" cy="34%" r="68%">
          <stop offset="0%" stop-color="#9BE8FF" />
          <stop offset="26%" stop-color="#4AB2DA" />
          <stop offset="58%" stop-color="#287B9F" />
          <stop offset="86%" stop-color="#0E3B54" />
          <stop offset="100%" stop-color="#061D2C" />
        </radialGradient>
        <linearGradient
          :id="ids.atmoRim"
          x1="53"
          y1="53"
          x2="147"
          y2="147"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0%" stop-color="#CFF4FF" stop-opacity="0.92" />
          <stop offset="50%" stop-color="#58B8DF" stop-opacity="0.35" />
          <stop offset="100%" stop-color="#0A2E42" stop-opacity="0.6" />
        </linearGradient>
        <linearGradient
          :id="ids.gold"
          x1="30"
          y1="100"
          x2="170"
          y2="100"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0%" stop-color="#C48A2C" />
          <stop offset="28%" stop-color="#F7D388" />
          <stop offset="65%" stop-color="#FFFDF7" />
          <stop offset="100%" stop-color="#D49836" />
        </linearGradient>
        <linearGradient
          :id="ids.goldBack"
          x1="30"
          y1="100"
          x2="170"
          y2="100"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0%" stop-color="#C48A2C" />
          <stop offset="50%" stop-color="#8C5E18" />
          <stop offset="100%" stop-color="#D49836" />
        </linearGradient>
        <clipPath :id="ids.planetClip">
          <circle cx="100" cy="100" r="47" />
        </clipPath>
      </defs>

      <rect width="200" height="200" rx="46" :fill="`url(#${ids.bg})`" />
      <rect
        width="198"
        height="198"
        x="1"
        y="1"
        rx="45"
        :stroke="`url(#${ids.rim})`"
        stroke-width="1.5"
      />

      <circle cx="100" cy="100" r="84" :fill="`url(#${ids.aura})`" />
      <circle
        cx="100"
        cy="100"
        r="84"
        stroke="#338AAF"
        stroke-opacity="0.16"
        stroke-dasharray="3 6"
      />
      <circle cx="100" cy="100" r="92" stroke="#FFFFFF" stroke-opacity="0.03" />

      <path
        d="M 38 34 V 42 M 34 38 H 42"
        stroke="#E5B66A"
        stroke-width="1.8"
        stroke-linecap="round"
        stroke-opacity="0.58"
      />
      <path
        d="M 162 34 V 42 M 158 38 H 166"
        stroke="#338AAF"
        stroke-width="1.8"
        stroke-linecap="round"
        stroke-opacity="0.68"
      />
      <path
        d="M 38 158 V 166 M 34 162 H 42"
        stroke="#338AAF"
        stroke-width="1.8"
        stroke-linecap="round"
        stroke-opacity="0.68"
      />
      <path
        d="M 162 158 V 166 M 158 162 H 166"
        stroke="#E5B66A"
        stroke-width="1.8"
        stroke-linecap="round"
        stroke-opacity="0.58"
      />

      <g transform="rotate(-24 100 100)">
        <path
          d="M 30 100 A 70 22 0 0 1 170 100"
          :stroke="`url(#${ids.goldBack})`"
          stroke-width="5.2"
          stroke-opacity="0.72"
          stroke-linecap="round"
        />
      </g>

      <circle cx="100" cy="104" r="47" fill="#02060C" fill-opacity="0.78" />
      <circle cx="100" cy="100" r="51" stroke="#4AB2DA" stroke-width="1.4" stroke-opacity="0.22" />
      <circle cx="100" cy="100" r="47" :fill="`url(#${ids.sphere})`" />

      <g :clip-path="`url(#${ids.planetClip})`">
        <g transform="rotate(-24 100 100)">
          <ellipse
            cx="100"
            cy="79"
            rx="42"
            ry="10.5"
            stroke="#B8EEFF"
            stroke-width="1.7"
            stroke-opacity="0.52"
            fill="none"
          />
          <ellipse
            cx="100"
            cy="121"
            rx="42"
            ry="10.5"
            stroke="#7BD4F5"
            stroke-width="1.5"
            stroke-opacity="0.34"
            fill="none"
          />
          <ellipse
            cx="100"
            cy="100"
            rx="22.5"
            ry="47"
            stroke="#CFF4FF"
            stroke-width="2.1"
            stroke-opacity="0.65"
            fill="none"
          />
          <line
            x1="100"
            y1="51"
            x2="100"
            y2="149"
            stroke="#FFFFFF"
            stroke-width="1.6"
            stroke-opacity="0.46"
          />
          <path
            d="M 30 104.5 A 70 22 0 0 0 170 104.5"
            stroke="#041521"
            stroke-width="8.5"
            stroke-opacity="0.5"
            fill="none"
          />
        </g>
        <circle cx="84" cy="84" r="6.5" fill="#FFFFFF" fill-opacity="0.24" />
        <circle cx="84" cy="84" r="3.2" fill="#FFFFFF" />
      </g>

      <circle cx="100" cy="100" r="46.25" :stroke="`url(#${ids.atmoRim})`" stroke-width="1.5" />

      <g transform="rotate(-24 100 100)">
        <path
          d="M 30 100 A 70 22 0 0 0 170 100"
          :stroke="`url(#${ids.gold})`"
          stroke-width="6.4"
          stroke-linecap="round"
        />
        <g transform="translate(146.84, 116.35)">
          <circle
            cx="0"
            cy="0"
            r="10.5"
            fill="#071926"
            fill-opacity="0.65"
            stroke="#67C7EB"
            stroke-width="1.6"
            stroke-opacity="0.88"
          />
          <circle cx="0" cy="0" r="5.8" fill="#FFFDF7" />
          <circle cx="0" cy="0" r="3" fill="#338AAF" />
        </g>
      </g>
    </svg>
    <span v-if="!iconOnly" class="cyber-logo__wordmark">
      <strong>{{ platformConfig.name }}</strong>
      <small v-if="showDescriptor">{{ platformConfig.tagline.toUpperCase() }}</small>
    </span>
  </span>
</template>

<script setup lang="ts">
import { useId } from 'vue'
import { appConfig as platformConfig } from '@/app/app.config'

withDefaults(
  defineProps<{
    iconOnly?: boolean
    showDescriptor?: boolean
    tone?: 'dark' | 'light'
  }>(),
  {
    iconOnly: false,
    showDescriptor: true,
    tone: 'light',
  },
)

const uid = useId()
const ids = {
  bg: `${uid}-bg`,
  aura: `${uid}-aura`,
  rim: `${uid}-rim`,
  sphere: `${uid}-sphere`,
  atmoRim: `${uid}-atmo-rim`,
  gold: `${uid}-gold`,
  goldBack: `${uid}-gold-back`,
  planetClip: `${uid}-planet-clip`,
}
</script>

<style scoped>
.cyber-logo {
  --cyber-logo-text: var(--hero-foreground);
  --cyber-logo-muted: var(--hero-meta);
  --cyber-logo-mark-size: 48px;
  display: inline-flex;
  align-items: center;
  gap: 13px;
}

.cyber-logo--dark {
  --cyber-logo-text: var(--ink);
  --cyber-logo-muted: var(--muted);
}

.cyber-logo--icon-only {
  display: inline-grid;
  place-items: center;
}

.cyber-logo__mark {
  display: block;
  width: var(--cyber-logo-mark-size);
  height: var(--cyber-logo-mark-size);
  flex: 0 0 auto;
}

.cyber-logo__wordmark {
  min-width: 0;
  display: grid;
  gap: 4px;
}

.cyber-logo__wordmark strong {
  color: var(--cyber-logo-text);
  font-family: var(--font-display);
  font-size: var(--cyber-logo-wordmark-size, 16px);
  font-weight: 760;
  letter-spacing: 0.22em;
  line-height: 1;
}

.cyber-logo__wordmark small {
  max-width: 220px;
  overflow-wrap: anywhere;
  line-height: 1.4;
  color: var(--cyber-logo-muted);
  font-size: var(--cyber-logo-descriptor-size, 8px);
  font-weight: 700;
  letter-spacing: 0.2em;
}
</style>
