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

## Email obfuscation (Alberti Encryption)
```python
def albenc(s):
    r = ''
    for i, ch in enumerate(s):
        if ord(ch) in range(32, 123):
            alpha_index = (ord(ch) - 32 + i) % (123 - 32)
            r += chr(alpha_index + 32)
        else:
            r += ch
    return r
s = albenc('amte2022@parsaamini.net')
print(s)

def albdec(s):
    r = ''
    for i, ch in enumerate(s):
        ch_i = ord(ch)
        if ch_i >= 32 and ch_i < 123:
            r += chr((ord(ch) - 32 - i) % (123 - 32) + 32)
        else:
            r += ch
    return r
albdec(s)
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