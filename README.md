# AMTE2022.github.io

## Making AMTE logo with ImageMagick
Font: [Overpass Black](https://fonts.google.com/specimen/Overpass)
```bash
magick -background none \
    -density 574 \
    -fill '#377cb8' \
    -font 'Overpass-Black.ttf' \
    label:'AMTE 2022' \
    -unsharp 0x.5 \
    -gravity southeast -splice 30x25 \
    -gravity northwest -splice 30x25 \
    logo.png
```
