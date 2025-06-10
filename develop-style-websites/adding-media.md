
# Adding Media Guide for Web Design

HTML provides methods to embed rich media, including images, audio, videos, and inline frames, enhancing plain text content.

## Adding Images
The `<img>` element is an inline, self-closing tag that embeds images using the `src` attribute (URL) and `alt` attribute (alternative text for accessibility).
```html
<img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief">
```
- **Supported Formats**: GIF, JPG, PNG.

### Sizing Images
Set dimensions using CSS `width` and `height`.
```css
img {
  height: 200px;
  width: 200px;
}
```

### Positioning Images
Use CSS properties like `float`, `display`, `padding`, `border`, and `margin` to position images.

#### Inline Positioning
Default behavior places the image inline with text.
```html
<p>Gatsby is a black, brown, and white hound mix puppy... <img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief"> Although he spends most of his time...</p>
```

#### Block Positioning
Set `display: block` to place the image on its own line.
```css
img {
  display: block;
}
```

#### Floating Images
Float images left or right to wrap surrounding content.
```css
img {
  background: #eaeaed;
  border: 1px solid #9799a7;
  float: right;
  margin: 8px 0 0 20px;
  padding: 4px;
}
```

### Image Element vs. Background Image
- `<img>`: Inline HTML element for content images.
- `background-image`: CSS property for decorative images.

## Adding Audio
The `<audio>` element embeds audio files using the `src` attribute.
```html
<audio src="jazz.ogg"></audio>
```
- **Supported Formats**: OGG, MP3, WAV.

### Audio Attributes
Boolean attributes include:
- `autoplay`: Plays audio on load.
- `controls`: Displays browser-default controls (play, pause, volume).
- `loop`: Repeats audio indefinitely.
- `preload`: Specifies preloading behavior (`none`, `auto`, `metadata`).
```html
<audio src="jazz.ogg" controls autoplay></audio>
```

### Audio Fallbacks & Multiple Sources
Use `<source>` elements to provide multiple formats with a fallback link.
```html
<audio controls>
  <source src="jazz.ogg" type="audio/ogg">
  <source src="jazz.mp3" type="audio/mpeg">
  <source src="jazz.wav" type="audio/wav">
  Please <a href="jazz.mp3" download>download</a> the audio file.
</audio>
```

## Adding Video
The `<video>` element embeds videos, supporting `src`, `autoplay`, `controls`, `loop`, and `preload` attributes, similar to `<audio>`. Dimensions should be specified.
```html
<video src="earth.ogv" controls></video>
```
- **Supported Formats**: OGV, MP4, WebM.

### Poster Attribute
Specify an image to display before the video plays.
```html
<video src="earth.ogv" controls poster="earth-video-screenshot.jpg"></video>
```

### Video Fallbacks
Provide multiple formats and a fallback link.
```html
<video controls>
  <source src="earth.ogv" type="video/ogg">
  <source src="earth.mp4" type="video/mp4">
  Please <a href="earth.mp4" download>download</a> the video.
</video>
```
- Custom controls require JavaScript and vary by browser.

## Adding Inline Frames
The `<iframe>` element embeds external content (e.g., maps, videos) using the `src` attribute.
```html
<iframe src="https://www.google.com/maps/embed?..."></iframe>
```
- **Attributes**: `width`, `height`, `frameborder` (to remove default borders).
- Links within an `<iframe>` stay within the frame.

## Semantically Identifying Figures & Captions
Use `<figure>` to group self-contained content (e.g., images, audio, videos) and `<figcaption>` for captions.
```html
<figure>
  <img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief">
  <figcaption>A beautiful black, brown, and white hound dog wearing a kerchief.</figcaption>
</figure>
```
```css
img {
  display: block;
  max-width: 100%;
}
```
- `<figcaption>` can appear at the top, bottom, or within `<figure>`.

## Summary
- **Images**: Use `<img>` with `src` and `alt`, style with CSS for size and positioning.
- **Audio/Video**: Use `<audio>` and `<video>` with attributes (`controls`, `autoplay`, etc.) and `<source>` for fallbacks.
- **Inline Frames**: Embed external content with `<iframe>`.
- **Figures & Captions**: Use `<figure>` and `<figcaption>` for semantic media grouping.





