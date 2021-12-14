<a href="https://beyonk.com">
    <br />
    <br />
    <img src="https://user-images.githubusercontent.com/218949/144224348-1b3a20d5-d68e-4a7a-b6ac-6946f19f4a86.png" width="198" />
    <br />
    <br />
</a>

## Svelte Trustpilot

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com) [![CircleCI](https://circleci.com/gh/beyonk-adventures/svelte-trustpilot.svg?style=shield)](https://circleci.com/gh/beyonk-adventures/svelte-trustpilot) [![svelte-v2](https://img.shields.io/badge/svelte-v2-orange.svg)](https://v2.svelte.dev) [![svelte-v3](https://img.shields.io/badge/svelte-v3-blueviolet.svg)](https://svelte.dev)

Pure vanilla JS Trustpilot integration

![trustpilot](https://user-images.githubusercontent.com/218949/51251849-2ea51080-1992-11e9-8683-d46ea7aa8bf6.png)

## Install

```bash
$ npm install --save-dev @beyonk/svelte-trustpilot
```

## Usage (With Svelte)

```html
<Trustpilot businessUnit="12345" domain="www.example.com"  />

<script>
  import Trustpilot from '@beyonk/svelte-trustpilot'
</script>
```

The attributes you pass to the Trusilot component are listed below, but you need `domain` and `businessUnit` at a minimum.

## Usage (Vanilla JS)

```html
<div id="trustpilot-wrapper"></div>

<script>
  import Trustpilot from '@beyonk/svelte-trustpilot'

	const trustpilot = new Trustpilot({
		target: document.querySelector('#trustpilot-wrapper'),
		data: {
			businessUnit: '12345',
			domain: 'www.example.com'
		}
	})
</script>
```

## Other configuration attributes

There are a number of configuration attributes you can pass, but all are optional.

List of possible options in the module:

| Option            | Default      | Required | Description                                                                                                                           |
|-------------------|--------------|----------|---------------------------------------------------------------------------------------------------------------------------------------|
| widget (1)        | micro-star   | false    | Widget type as per [https://businessapp.b2b.trustpilot.com/?locale=en-US#/integrations/trustbox/library](Trustpilot Trustbox library) |
| domain            | -            | true     | Sets the domain/product name on Trustpilot (for the link when a user clicks your widget)                                              |
| businessUnit      | -            | true     | Sets `data-businessunit-id` as per docs                                                                                               |
| width             | 100%         | false    | Sets `data-style-width` as per docs                                                                                                   |
| height            | 500px        | false    | Sets `data-style-height` as per docs                                                                                                  |
| theme             | dark         | false    | Sets `data-theme` as per Trustpilot docs                                                                                              |
| lib               | package-name | false    | Unique id to determine if component is loaded. You probably don't need to change this.                                                |
| version           | v5           | false    | Trustpilot SDK version (best not to change)                                                                                           |
| * (2)             | -            | false    | Pass any other parameter you want here. See below.                                                                                    |

1) You can pass any widget template name in its hyphenated form, or, just pass the template id here instead. You can get the template id from the trustpilot integration url:

`https://businessapp.b2b.trustpilot.com/?locale=en-US#/integrations/trustbox/configuration/<widget-id-is-here>`

2) You can pass any `data-` attribute you normally pass to Trustpilot's widgets. These will be passed verbatim to the underlying widget HTML.

## License

[MIT License](./LICENSE)
