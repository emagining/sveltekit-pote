# Portable Text for Svelte & SvelteKit

Provides a way to render [Portable Text](http://www.portabletext.org) in Svelte / SvelteKit applications.

Based on [@arzidava/svelte-portable-text](https://github.com/arzidava/svelte-portable-text) but removes the wrapping `<div>` around blocks (paragraphs)
=> "p" blocks will be wrapped in `<p> {paragraph} </p>` instead of `<div><p><span> {paragraph} </span></p></div>`

## Install

```
npm add --save-dev @emagining/sveltekit-pote
```

## Usage

```html
<script>
  import BlockContent from '@emagining/sveltekit-pote'

  import Image from '$lib/Image.svelte'
  import Link from '$lib/Link.svelte'

  export let content;
  export const customSerializers = {
    types: {
      image: props => {
        return {
          component: Image,
          props: {
            url: props.node.url,
          },
        };
      },
    },
    marks: {
      link: props => {
        return {
          component: Link,
          props: props.mark,
        };
      },
    },
  };
</script>

<BlockContent blocks="{content}" serializers="{customSerializers}" />
```

## Work in Progress

This package was created to serve my own needs. 
### Todo: 
[] find a way to remove the span tag

Have a look at these libs to see if they better serve your need:

- [@arzidava/svelte-portable-text](https://github.com/arzidava/svelte-portable-text)
- [@movingbrands/svelte-portable-text](https://github.com/movingbrands/svelte-portable-text)

## Contribute
Open an issue or make a pull req. :)