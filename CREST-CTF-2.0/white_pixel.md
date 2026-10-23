## White Pixel — CTF Writeup

**Flag:** `crest{p}`

### Approach

The challenge presented a completely white webpage. Inspecting the source revealed an image at `/q.png`.

Downloaded the image:

```bash
curl -s http://2.31.70.16:5500/q.png -o q.png
```

The PNG was only **158 bytes**, with dimensions of 60×84 pixels.

Analyzing its RGB values revealed two colors:
- `(255,255,255)` — Pure white
- `(255,255,254)` — Almost white

The difference was just **1 in the blue channel**, making the hidden pixels invisible to the naked eye.

Used Python to reveal them:

```python
from PIL import Image

im = Image.open("q.png").convert("RGB")

for y in range(im.height):
    for x in range(im.width):
        pixel = im.getpixel((x, y))
        im.putpixel(
            (x, y),
            (0, 0, 0) if pixel != (255,255,255)
            else (255,255,255)
        )

im.save("revealed.png")
```

The resulting image revealed the letter **P**, encoded using near-white pixels.

### Flag

```text
crest{p}
```
