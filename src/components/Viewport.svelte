<style lang="scss">
  @import '../styles/base';
  #viewport {
    @include viewport;
    @include flexCenterAll;
    @include gradientFire;
    flex-direction: column;
    position: relative;
    z-index: -9999;

    h1 {
      @include flexCenterAll;
      text-align: center;
      font-size: 2.5rem;
      color: $light;
      text-shadow: .25rem .25rem .5rem $black;
    }
  }
</style>

<script lang="ts">
  import type { SvelteComponentDev } from 'svelte/internal'
  import type { IPhotoParams } from './interfaces'

  import Home from '../routes/Home.svelte'
  import About from '../routes/About.svelte'
  import Particles from './Particles.svelte'

  import router from 'page'
  export const appName = 'Wedington Photography'

  /* Routing */
  let page: typeof SvelteComponentDev

  // This will be used for more complex, authenticated routing later
  let params: IPhotoParams
  console.info('Params: %j', { params })
  // This will be used for more complex, authenticated routing later

  router('/', () => (page = Home))

  router('/about', () => (page = About))

  router.start()
  /* Routing */

</script>

<div id="viewport">
  <h1>{appName}</h1>
  <svelte:component this={page} />
  <Particles />
</div>

