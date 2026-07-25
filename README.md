# Etch A Sketch

A browser-based Etch A Sketch.

![Idle screen](screenshots/idle.png)

## Try it

Open `Etch.dc.html` in a browser.

## Controls

- **A / D** or **←/→** — move horizontal
- **W / S** or **↑/↓** — move vertical
- Drag the knobs directly with your mouse or finger, they have real momentum
- **Hold Space** — shake the whole thing and erase the screen
- Shaking the mouse back and forth fast enough also triggers an erase
- On a phone or tablet with a motion sensor, physically shaking the device erases it too

![Mid-doodle](screenshots/doodle.png)

## Draw an image

Hit **Draw Image**, pick a picture, and the toy draws it for you — centred on the
screen, by turning its own knobs. Nothing is pasted onto the canvas; every mark
comes out of the same stylus a person drives by hand. The picture itself never
appears on the screen; the only thing that shows up there is the drawing.

It goes in three beats, the same ones you'd do yourself:

1. The knobs crank the stylus over to where the drawing starts, leaving a travel line.
2. The case shakes and clears — which takes that travel line with it.
3. The picture goes down, stroke by stroke.

**1× / 2× / 4×** sets the pace. Click it, or press <kbd>1</kbd>, <kbd>2</kbd> or
<kbd>4</kbd> while it draws — the change lands immediately. Any key, either knob,
or **Stop** hands control back to you and keeps whatever got drawn.

A real Etch A Sketch can never lift its stylus, and neither does this one. The
image is traced into contours and then joined into one unbroken path, so the
faint straight lines hopping between separate shapes are supposed to be there —
that's the toy being honest.

They're kept short, though. Most traced contours turn out to be loops, and a
loop can be joined anywhere along itself, so each one is entered beside wherever
the stylus already is rather than at whatever pixel the tracer happened to open
it at. Having gone all the way round, the stylus carries on round to the point
nearest whatever it draws next — retracing a line already down, which costs
nothing to look at. What's left is judged by the square of its length, because
one line ruled across the middle of a drawing spoils it more than a dozen little
nicks between neighbouring strokes.

### Photographs with something going on behind them

A picture taken somewhere — a park, a room, a street — used to come out as mush,
because the ink went on leaves and brickwork before it got anywhere near the
subject. Those now get the subject lifted out first.

It picks where to look by itself. Then two floods rise through the image at
once, one from that point and one from the edges of the frame, and every pixel
joins whichever reaches it first over the lowest ground. Where they meet is the
outline. Being a race rather than a one-sided fill is the point — a soft edge
costs the background the pixel instead of handing it the picture, and the
boundary comes out closed because every pixel ends up on one side or the other.

It only tries this when the background is busy enough to be worth removing. On a
white page or a plain wall there's no background ink to save, so cutting one out
could only lose you part of a logo — those get drawn whole, exactly as before.
And a guess that comes back scattered rather than looking like a single thing is
thrown away, because the wrong cutout is much worse than none: refusing just
draws the whole picture, while believing a bad one draws somebody's haircut
floating above their shirt.

### How it reads a picture

This toy has no grey. The stylus is down or it isn't, so the picture is made to
decide the same thing before anything is traced:

1. **It goes black and white.** Every pixel is judged against the average of its
   own neighbourhood rather than one cutoff for the whole picture, so a face lit
   from one side keeps both cheeks instead of losing the shaded one to solid
   black. A transparent PNG's cutout is respected if there is one.
2. **Then it traces**, in three grades: the borders between the black and the
   white, then whatever soft tonal edges the threshold flattened away.

Borders of a black-and-white image close on themselves, which is why circles come
out as circles here. Chasing gradients across the original photo gives you open,
broken fragments of the same shapes.

A line only counts if there's really an edge under it. Threshold a smooth
gradient — the side of a mug, a cheek turning away from the light — and you get
a confident line where the tone crosses its own average, corresponding to nothing
you can actually see. Those get dropped.

That order is also the priority. There's only so much line you can lay down
before a drawing turns to mush, so it spends an ink budget and stops: the shape
of the thing survives, fine detail is what gets dropped. A logo keeps everything.
High-contrast pictures, logos and line drawings come out sharpest.

The budget isn't the same for every picture. It's set by how much line the
picture is asking for — structure counted in full, fine detail at a third —
and a busy one earns up to four times the room a simple one gets. The weighting
matters: a stained-glass window and a grainy snapshot can want the same total
length of line, but one is asking for borders and the other for the last of its
noise, and only the first is worth more ink. Nothing ever gets less than it used
to; most pictures never come near the limit anyway.
