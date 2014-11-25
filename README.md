# tilelive-merge

A tilelive source that merges sources.

Overzooming (using part of a lower-zoom tile), masking (falling back to
lower-zoom tiles when they're intentionally missing, as in the middle of the
ocean), and image layers are all supported and the most conservative upstream
values for `Last-Modified` and `Cache-Control` are used.

## Usage

```
merge:?source=mapbox:///mapbox.mapbox-streets-v5&source=tilejson%2Bhttp%3A%2F%2Ftile.stamen.com%2Ftoner-labels%2Findex.json
```

The full-on explicit way (avoids having to encode URIs with
`encodeURIComponent` in some circumstances--this is the same as `url.parse(uri,
true)`):

```javascript
{
  protocol: "merge:",
  query: {
    sources: [
      "mapbox:///mapbox.mapbox-streets-v5",
      "tilejson+http://tile.stamen.com/toner-labels/index.json"
    ]
  }
}
```

(Yes, both `source` and `sources` work.)
