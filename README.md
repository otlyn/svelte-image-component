# Svelte Image Component

An image component for svelte using best practices for responsive images. Additionally, built with placeholder functionality for quick prototyping.

## How it works

The image paths, suffixes and sizes are hardcoded. So writing this:

<!-- prettier-ignore -->
```html
<Image src="image" alt="Description" />
```

Compiles to this:

```html
<img
  src="images/image-md.jpg"
  srcset="
    images/image-sm.jpg  600w,
    images/image-md.jpg 1200w,
    images/image-lg.jpg 2400w
  "
  alt="Description"
/>
```

## Alt Fallback

The `alt` attribute should always be filled out, but if it's not it will default to the file name. The following:

<!-- prettier-ignore -->
```html
<Image src="image" />
```

Compiles to this:

```html
<img
  src="images/image-md.jpg"
  srcset="
    images/image-sm.jpg  600w,
    images/image-md.jpg 1200w,
    images/image-lg.jpg 2400w
  "
  alt="image"
/>
```

## Placeholder images

There are three placeholder image options:

- `landscape`
- `portrait`
- `sqaure`

And can be used as follows:

<!-- prettier-ignore -->
```html
<Image landscape={true} />

<Image portrait={true} />

<Image square={true} />
```

## Overwrite for Prototyping

By default, placeholder images will overwrite `src` images. For example, the following will output a landscape placeholder, despite having `src="image"`.

<!-- prettier-ignore -->
```html
<Image src="image" landscape="{true}" />
```
