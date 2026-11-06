### Challenge

I revealed the information hidden in the nearly white image at `/q.png`.

### Solve

I downloaded the image and compared its RGB values. I found hidden pixels at `(255, 255, 254)`, one blue-channel value below white. I rendered each non-white pixel black:

```bash
curl -s http://<challenge-host>/q.png -o q.png
```

```python
from PIL import Image

image = Image.open("q.png").convert("RGB")
pixels = image.load()

for y in range(image.height):
    for x in range(image.width):
        if pixels[x, y] != (255, 255, 255):
            pixels[x, y] = (0, 0, 0)

image.save("revealed.png")
```

The resulting image showed `P`.

### Flag

```text
crest{p}
```
