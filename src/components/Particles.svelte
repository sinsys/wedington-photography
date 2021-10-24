<script type="ts">
  // TODO: Hardcoded scaffolding below. Needs refactor for expansion.
  const particleCount = 4
</script>

<div class="particle-wrapper">
  {#each Array(particleCount) as _, i}
    <div class="particle particle-{i}"></div>
  {/each}
</div>

<style lang="scss">
  @import '../styles/colors';

  $color-particle: $dark;
  $spacing: 1600px;
  $time-1: 20s;
  $time-2: 30s;
  $time-3: 60s;
  $time-4: 200s;
  $particle-1-count: 100;
  $particle-2-count: 50;
  $particle-3-count: 25;
  $particle-4-count: 10;

  // Space, anim, randomness (you know, particles)
  @function particles($max) {
    $val: 0px 0px $color-particle;
    @for $i from 1 through $max {
      $val: #{$val},
      random($spacing)+px random($spacing)+px $color-particle;
    }
    @return $val;
  }

  @mixin particles($max) {
    box-shadow: particles($max);
  }

  .particle-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: -1;
  }

  .particle,
  .particle:after {
    background: transparent;
    transition: all;
  }

  .particle:after {
    position: absolute;
    content: "";
    top: $spacing;
  }

  .particle-1, .particle-2, .particle-3, .particle-4 {
    animation-direction: alternate;
  }

  .particle-1 {
    animation: animParticle $time-1 ease-in-out infinite;
    @include particles($particle-1-count);
    height: 1rem;
    width: 1.5rem;
    opacity: 0.1;
  }

  .particle-1:after {
    @include particles($particle-1-count);
    height: 1rem;
    width: 1.5rem;
    opacity: 0.1;
  }

  .particle-2 {
    animation: animParticle $time-2 ease-in-out infinite;
    @include particles($particle-2-count);
    height: 3rem;
    width: 4.5rem;
    opacity: 0.15;
  }

  .particle-2:after {
    @include particles($particle-2-count);
    height: 3rem;
    width: 4.5rem;
    opacity: 0.15;
  }

  .particle-3 {
    animation: animParticle $time-3 ease-in-out infinite;
    @include particles($particle-3-count);
    height: 4rem;
    width: 6rem;
    opacity: 0.2;
  }

  .particle-3:after {
    @include particles($particle-3-count);
    height: 4rem;
    width: 6rem;
    opacity: 0.2;
  }

  .particle-4 {
    animation: animParticle $time-4 ease-in-out infinite;
    @include particles($particle-4-count);
    height: 8rem;
    width: 12rem;
    opacity: 0.3;
  }

  .particle-4:after {
    @include particles($particle-4-count);
    height: 8rem;
    width: 12rem;
    opacity: 0.3;
  }

  @keyframes animParticle {
    0% {
      transform: translateY($spacing * -0.5) translateX(0px);
    }
    25% {
      transform: translateY($spacing * -0.2) translateX(-25vw);
    }
    50% {
      transform: translateY(0px) translateX(0px);
    }
    75% {
      transform: translateY($spacing * -0.3) translateX(25vw);
    }
    100% {
      transform: translateY($spacing * -0.5) translateX(0px);
    }
  }
</style>