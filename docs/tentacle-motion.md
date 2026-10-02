# Tentacle motion: reference principles

A working reference for how Swell's jellyfish tentacles should move, distilled from the reference footage, animation principles and the iterations so far. Principles only; no formulas.

## What a tentacle is

- A tentacle is a passive, flexible strand hanging in water. Apart from the rim it grows from, it has no muscles of its own. Everything it does comes from two sources: the rim moving it, and the water resisting it.
- Water is the dominant force. It is thick: it damps motion, holds each part of the strand roughly where it was, and lets motion arrive gradually. Inertia and gravity are minor by comparison.
- It is thin and light toward the tip. So the tip is the most responsive part: it ends up with the widest swing and a little flick, and settles last.

## Where motion comes from

- **The root is driven; the rest is dragged.** The rim margin moves the root: outward and open as the bell flares on the inhale, inward and tucked as it snaps shut on the push.
- **The root continues the bell.** The strand leaves the rim tangent to the bell margin, so bell and tentacle read as one continuous curve. There is never a kink or an opposing bend at the joint.
- **The body's own movement through the water** is the other driver. When the jellyfish lunges upward, water streams past and pulls the strands down and together behind it. When it glides and slows, they loosen and spread.

## How motion travels

- **Successive breaking of joints.** Motion starts at the root and passes down the strand one section at a time at a finite speed. A section does not move until the motion reaches it.
- **The tip never leads.** If the tip moves before the bend arrives, the strand is behaving like a rigid lever. That is the classic forward-kinematics mistake: rotating a joint carries everything below it instantly. Water prevents that, because the lower strand is held in place while the upper strand bends to connect to it.
- **Follow-through.** The tips keep moving after the bell has stopped, then settle. Nothing stops all at once.
- **Overlapping action.** Neighbouring strands are slightly out of step. No two move in perfect unison.

## Shapes to expect

- **The working shape is a smooth S** whose bends are on the scale of the whole strand: about one S per strand. These shapes are wrong:
  - a C bent as a single lever;
  - a straight line with a small dip travelling down it (bends too small);
  - a line with several small wiggles (wavelength too short).
- **Inhale (slow opening):** the rim flares and swings the roots outward. The lower strand is still hanging where it was, so the upper strand angles out and curves back down to meet it. The S builds from the top down. This is the load: the anticipation of the push.
- **Push (fast closing):** the rim snaps in and the roots tuck first. The outward bend from the inhale is still travelling down the strand, so the strand is in at the top and out below. That is the S. As it travels, the tight bend near the root lengthens into a broad arch and reaches the tips as follow-through.
- **Glide:** the body is moving, so the strands trail behind and streamline. As it slows they relax into gentle curves. They never go dead straight.
- **At rest:** strands hang loosely in gentle curves, with slight drift from the water. They are alive, not rigid.

## Strand roles in the footage

- **Thin rim tentacles** are the active ones: S-curves, travelling waves, flick at the tips.
- **Thick central strands** are longer, straighter and slower, with broad, lazy kinks. (Swell has no central oral arms, so at most this means slightly calmer middle strands.)

## Crossing

- In 3D, strands pass in front of and behind each other all the time. A flat "never cross" rule fights natural motion. It is switched off until the motion is right, and will then come back in a form that does not distort the shapes (for example, layering instead of shoving).

## Bad assumptions that accumulated

- **Propagating an angle and integrating it down the chain.** Any change near the root then swings the whole lower strand at once (the lever effect).
- **Delaying different things by different amounts.** For example, root position delayed less than root angle. The lower strand then moves before the bend reaches it.
- **Tying wave speed to the breath period.** Wave speed belongs to the water and the strand, not to how slowly someone breathes. A 10 s breath made the wave creep.
- **Faking the result directly.** Hand-shaping an S, adding standing ripples, or smoothing kinks after the fact. Each fix met one complaint and broke another.
- **Writing the shape as a formula of time.** The strand should be a physical thing with state, driven at the root and resisted by water. The shapes above should emerge from that rather than being drawn on.

## Approach

- Each strand is a chain of short, fixed-length links with memory of where it was (a simulated strand in water).
- The rim drives the root section: its position, plus its angle tangent to the margin.
- Water resists every link's movement relative to the surrounding flow. That flow includes the body's own speed through the water and a slow ambient drift.
- Slight stiffness keeps curves smooth. It is stiffer near the root and softer toward the tip.
- The guide and your jellyfish run the same strand model. Only the bell motion driving it differs.
