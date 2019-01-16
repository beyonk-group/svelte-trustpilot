<p align="center">
  <img width="186" height="90" src="https://user-images.githubusercontent.com/218949/44782765-377e7c80-ab80-11e8-9dd8-fce0e37c235b.png" alt="Beyonk" />
</p>

## Svelte Trustpilot

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com) [![CircleCI](https://circleci.com/gh/beyonk-adventures/svelte-trustpilot.svg?style=shield)](https://circleci.com/gh/beyonk-adventures/svelte-trustpilot)


Pure vanilla JS Trustpilot integration

![Trustpilot](![trustpilot](https://user-images.githubusercontent.com/218949/51251143-80e53200-1990-11e9-8aa0-e05e9bf19bcb.png) "Trustpilot")

## Install

```bash
$ npm install --save-dev @beyonk/svelte-trustpilot
```

## Usage (With Svelte)

```html
<Trustpilot businessUnit="12345" domain="www.example.com"  />

<script>
  import Trustpilot from '@beyonk/svelte-trustpilot'

	export default {
		components: {
			Trustpilot
		}
	}
</script>
```

The attributes you pass to the Trusilot component are listed below, but you need `domain` and `businessId` at a minimum.

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
| widget            | micro-star   | false    | Widget type as per [https://businessapp.b2b.trustpilot.com/?locale=en-US#/integrations/trustbox/library](Trustpilot Trustbox library) |
| width             | 100%         | false    | Sets `data-style-width` as per docs                                                                                                   |
| height            | 500px        | false    | Sets `data-style-height` as per docs                                                                                                  |
| theme             | dark         | false    | Sets `data-theme` as per Trustpilot docs                                                                                              |
| lib               | package-name | false    | Unique id to determine if component is loaded. You probably don't need to change this.                                                |
| version           | v5           | false    | Trustpilot SDK version (best not to change)                                                                                           |

## License

[MIT License](./LICENSE)
