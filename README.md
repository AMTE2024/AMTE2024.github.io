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
    label:'<email address>' \
    -resample 72 \
    -unsharp 0x.5 \
    -gravity northwest \
    -splice 0x25 \
    /Users/parsa/Repositories/stellargroup/AMTE2023.github.io/workshop_contact.png
```

## Email obfuscation (Modified Alberti Cipher)

Modifications to the Alberti cipher:
1. Instead of the key used in the Alberti cipher, the key is simply a formula of $3*i+31$ to get the index of the character in the alphabet.
2. The alphabet is extended to include the characters `@_-+.`

```python
alphabet = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@_-+."


def slide_pos(x):
    return 3 * x + 31


def albenc(message):
    ciphertext = ""
    for i, ch in enumerate(message):
        if ch in alphabet:
            alpha_index = (alphabet.index(ch) + slide_pos(i)) % len(alphabet)
            ciphertext += alphabet[alpha_index]
        else:
            ciphertext += ch
    return ciphertext


ciphertext = albenc("<input plaintext>")
print(ciphertext)
assert ciphertext == "<cipher>"


def albdec(ciphertext):
    plaintext = ""
    for i, ch in enumerate(ciphertext):
        if ch in alphabet:
            plaintext += alphabet[(alphabet.index(ch) - slide_pos(i)) % len(alphabet)]
        else:
            plaintext += ch
    return plaintext


plaintext = albdec(ciphertext)
print(plaintext)

```

Readable JavaScript version:
```javascript
// Define the character sets
var alphabet = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@_-+.";
var encodedString = "<cipher>";

// Initialize the decoded string
let decodedString = "";

// Loop through each character in the encoded string and decode it
for (let i = 0; i < encodedString.length; i++) {
    var encodedChar = encodedString.charAt(i);
    var encodedCharOffset = 3 * i + 31;
    var encodedCharIndex = alphabet.indexOf(encodedChar);
    var decodedCharIndex = (encodedCharIndex - encodedCharOffset + alphabet.length) % alphabet.length;
    var decodedChar = alphabet.charAt(decodedCharIndex);
    decodedString += decodedChar;
}

// Display the decoded string in the HTML element with ID "cntc"
var cntcElement = document.getElementById("cntc");
cntcElement.textContent = decodedString;
```

Minified JavaScript version:
```javascript
var d = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@_-+.";
var s = "<cipher>"
var r = ""
for (var i = 0; i < s.length; i++) r += d.charAt((((d.indexOf(s.charAt(i)) - (3 * i + 31)) + d.length) % d.length));
document.getElementById("cntc").textContent = r;
```
