# Svelte Image Component

An image component for svelte using best practices for responsive images. Additionally, built with placeholder functionality for quick prototyping.

## How it works

The image paths, suffixes and sizes are hardcoded. So writing this:

<!-- prettier-ignore -->
```html
<Image src="image.jpg" alt="Description" />
```

Compiles to this:

```html
<img
  src="images/image@md.jpg"
  srcset="
    images/image@xs.jpg  150w,
    images/image@sm.jpg  300w,
    images/image@md.jpg  600w,
    images/image@lg.jpg 1200w,
    images/image@xl.jpg 2400w
  "
  alt="Description"
/>
```

## Alt Fallback

The `alt` attribute should always be filled out, but if it's not it will default to the file name. The following:

<!-- prettier-ignore -->
```html
<Image src="image.jpg" />
```

Compiles to this:

```html
<img
  src="images/image@md.jpg"
  srcset="
    images/image@xs.jpg  150w,
    images/image@sm.jpg  300w,
    images/image@md.jpg  600w,
    images/image@lg.jpg 1200w,
    images/image@xl.jpg 2400w
  "
  alt="image"
/>
```

## Specify size for best optimization

The options are `sm`, `md`, `lg`, and should be written like so:

<!-- prettier-ignore -->
```html
<Image src="image.jpg" size="sm" />

<Image src="image.jpg" size="md" />

<Image src="image.jpg" size="lg" />
```

These will compile to:

```html
<img
  src="images/image@sm.jpg"
  srcset="
    images/image@xs.jpg 150w,
    images/image@sm.jpg 300w,
    images/image@md.jpg 600w
  "
  alt="image"
/>

<img
  src="images/image@md.jpg"
  srcset="
    images/image@sm.jpg  300w,
    images/image@md.jpg  600w,
    images/image@lg.jpg 1200w
  "
  alt="image"
/>

<img
  src="images/image@lg.jpg"
  srcset="
    images/image@md.jpg  600w,
    images/image@lg.jpg 1200w,
    images/image@xl.jpg 2400w
  "
  alt="image"
/>
```

## Placeholder images (coming soon...)

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
