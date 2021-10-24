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
      font-size: 2.5rem;
      color: $light;
      text-shadow: .25rem .25rem .5rem #131313;
    }
  }
</style>

<script lang="ts">
  import type { SvelteComponentDev } from 'svelte/internal'
  import type { IPhotoParams } from './interfaces'
  import { onMount } from 'svelte'

  import Home from '../routes/Home.svelte'
  import About from '../routes/About.svelte'
  import Photo from '../routes/Photo.svelte'
  import Particles from './Particles.svelte'

  import router from 'page'
  export const appName = 'Wedington Photography'

  /* Routing */
  let page: typeof SvelteComponentDev
  let params: IPhotoParams

  router('/', () => (page = Home))

  router('/about', () => (page = About))

  router(
    '/photo/:id',
    (ctx, next) => {
      if (ctx?.params != null) {
        params = ctx?.params as IPhotoParams
      }
      next()
    },
    () => (page = Photo)
  )

  router.start()
  /* Routing */

  const getID = () => {
    console.log(params.id)
  }

  onMount(() => getID())
</script>

<div id="viewport">
  <h1>{appName}</h1>
  <svelte:component this={page} />
  <Particles />
</div>

