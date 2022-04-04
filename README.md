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
    assets/logo.png
```
## Making contact email images with ImageMagick
```bash
magick -background none \
    -density 196 \
    -font /System/Library/Fonts/Menlo.ttc \
    label:'amte2022@parsaamini.net' \
    -resample 72 \
    -unsharp 0x.5 \
    -gravity northwest \
    -splice 0x25 \
    /Users/parsa/Repositories/stellargroup/AMTE2022.github.io/workshop_contact.png
```

