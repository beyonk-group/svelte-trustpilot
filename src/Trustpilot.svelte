<div 
  style="width: {width}; height: {height};"
  bind:this={widgetElement}
  class="trustpilot-widget"
  class:hidden={hidden}
  data-locale="en-GB"
  data-template-id={templateId(widget)}
  data-businessunit-id={businessUnit}
  data-style-height={height}
  data-style-width={width}
  data-theme={theme}
  >
    <a href="https://uk.trustpilot.com/review/{domain}" target="_blank" rel="external">Trustpilot</a>
</div>

<style>
  .trustpilot-widget {
    margin: 24px 0;
  }

  div {
    visibility: visible;
  }

  .hidden {
    visibility: hidden;
  }
</style>

<script>
  import { onMount } from 'svelte'
  import loader from '@beyonk/async-script-loader'
  const globalName = 'Trustpilot'

  export let height = '500px'
  export let width = '100%'
  export let widget = 'micro-star'
  export let businessUnit = null
  export let domain = null
  export let version = 'v5'
  export let theme = 'dark'

  let widgetElement
  let hidden = true

  onMount(() => {
    loader(
      `//widget.trustpilot.com/bootstrap/${version}/tp.widget.bootstrap.js`,
      () => { return window.hasOwnProperty(globalName) },
      () => {
        hidden = false
        window[globalName].loadFromElement(widgetElement)
      }
    )
  })

  function templateId (widget) {
    return {
      'micro-star': '5419b732fbfb950b10de65e5',
      'list': '539ad60defb9600b94d7df2c',
      'micro-button': '5419b757fa0340045cd0c938',
      'micro-combo': '5419b6ffb0d04a076446a9af',
      'micro-review-count': '5419b6a8b0d04a076446a9ad',
      'micro-trustscore': '5419b637fa0340045cd0c936',
      'mini': '53aa8807dec7e10d38f59f32',
      'review-collector': '56278e9abfbbba0bdcd568bc',
      'starter': '5613c9cde69ddc09340c6beb'
    }[widget] || widget
  }
</script>