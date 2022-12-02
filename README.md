# AMTE2023.github.io

## Making AMTE logo with ImageMagick
Font: [Overpass Black](https://fonts.google.com/specimen/Overpass)
```bash
magick -background none \
    -density 574 \
    -fill '#377cb8' \
    -font 'Overpass-Black.ttf' \
    label:'AMTE 2023' \
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
    label:'amte2023@parsaamini.net' \
    -resample 72 \
    -unsharp 0x.5 \
    -gravity northwest \
    -splice 0x25 \
    /Users/parsa/Repositories/stellargroup/AMTE2023.github.io/workshop_contact.png
```

## Email obfuscation (Alberti Encryption)
```python
d = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@_-+.";
# s = "FU4SEFKNYg9osdgvuCAuLFX"

def albenc(s):
    r = ''
    for i, ch in enumerate(s):
        if ch in d:
            alpha_index = (d.index(ch) + 3 * i + 31) % len(d)
            r += d[alpha_index]
        else:
            r += ch
    return r
s = albenc('amte2023@parsaamini.net')
print(s)

def albdec(s):
    r = ''
    for i, ch in enumerate(s):
        if ch in d:
            r += d[(d.index(ch) - 3 * i - 31) % len(d)]
        else:
            r += ch
    return r
print(albdec(s))
```

```javascript
var d = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@_-+.";
s = "<albenc output>"
var r = ""
for (var i = 0; i < s.length; i++)
  r += d.charAt(((((d.indexOf(s.charAt(i)) - (3 * i + 31)) % d.length) + d.length) % d.length));
e = document.getElementById("cntc");
e.textContent = r;
```