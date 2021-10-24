<style lang="scss">
  @import '../styles/base';
  #viewport {
    @include viewport;
    @include flexCenterAll;
    flex-direction: column;
  }
</style>

<script lang="ts">
  import type { SvelteComponentDev } from 'svelte/internal'
  import type { IPhotoParams } from './interfaces'

  import { onMount } from 'svelte'
  import Home from '../routes/Home.svelte'
  import About from '../routes/About.svelte'
  import Photo from '../routes/Photo.svelte'

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
</div>
