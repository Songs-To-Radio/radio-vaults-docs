# Radio Vaults NFT Metadata Integration Documentation

## Overview

This document is intended for NFT Marketplaces looking to integrate with Radio Vaults' NFT Metadata structure. The goal is to ensure that the metadata associated with each NFT is displayed accurately and consistently across different platforms. The metadata structure includes details about the media, such as its name, description, image, and type, as well as links to additional content and attributes detailing more specifics about the media.

### Metadata Structure

Below is the structure of the metadata that Radio Vaults intakes for each NFT:

```json
{
    "name": "string", // Media name
    "description": "string",
    "image": "string", // image URL
    "media": "string", // link to Radio Vaults' webpage with media
    "media_type": "string", // also MIME-type
    "attributes": [{ "trait_type": "string", "value": "any" }], // more details on the song
    "external_url": "string" // URL provided by the creator
}
```

## Integration Guide

### Displaying Basic Information

The basic information includes the `name`, `description`, and `image` of the media. The following example illustrates how to render these details on a webpage.

```html
<!-- Sample HTML snippet for basic media information -->
<div class="nft-media-info">
    <h1 id="media-name"><!-- Media name will go here --></h1>
    <p id="media-description"><!-- Media description will go here --></p>
    <img id="media-image" src="" alt="Media Image">
</div>

<script>
// JavaScript to set the basic media information
const nftMetadata = { /* ... */ }; // The NFT metadata object
document.getElementById('media-name').textContent = nftMetadata.name;
document.getElementById('media-description').textContent = nftMetadata.description;
document.getElementById('media-image').src = nftMetadata.image;
</script>
```
The `media_type` property can be used by the frontend to know before hand the kind of media on the webpage that would be displayed via the iframe.

### Embedding Media

To display the media, it should be embedded using an `iframe`. The `media` property contains the URL to the Radio Vaults webpage where the media can be played, and should be used as the `src` for the `iframe`.
We do this to be able to track interactions for NFT creators and display statistics on their dashboards.

```html
<!-- Sample HTML snippet for embedding media -->
<iframe id="media-player" 
        src="" 
        width="640" 
        height="360" 
        frameborder="0" >
</iframe>

<script>
// JavaScript to set the media URL
const nftMetadata = { /* ... */ }; // The NFT metadata object
document.getElementById('media-player').src = nftMetadata.media;
</script>
```


## Conclusion

This guide provides the essential steps for integrating Radio Vaults' NFT Metadata within NFT Marketplaces. By following these steps, you can ensure that the metadata is displayed properly, providing end-users with a rich and informative experience. Make sure to test the integration thoroughly across different devices and browsers to ensure compatibility and responsiveness.
