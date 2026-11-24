# Touch: a tick and a sound

Principle 20 lets a touch answer with one short tick, felt on a phone or heard as a sound. Both are optional. Offer them; add them only when the user wants them.

## Tick

Where `navigator.vibrate` exists, call `navigator.vibrate(10)` from the tap or from each step of a drag. iPhone has no vibration API. The only route there is a workaround: the finger lands on an invisible `<label>` laid over the control, and that label belongs to a hidden `<input type="checkbox" switch>`, which ticks when it flips. It gives one tick per tap and nothing while dragging, and Apple may close it, so no control may depend on it. Give a dragged control tappable steps if it should tick on iPhone.

## Sound

Synthesise it with the Web Audio API, so there are no files to ship, and create the `AudioContext` inside the first tap, because a browser allows nothing sooner. Put a sound switch on the page and remember the choice. Never play a sound that is not the answer to a touch.

The sound is one soft knock: a sine that falls in pitch, with a few milliseconds of filtered noise on top. The noise is what carries it on a phone speaker.

```js
// f: register (1 = 300 Hz), d: length (1 = 70 ms), c: click, g: level, bend: where the pitch ends
function knock(ac, out, noiseBuffer, f, d, c, g, bend) {
  var t = ac.currentTime + 0.004, len = Math.max(0.018, 0.07 * d);
  var o = ac.createOscillator(), e = ac.createGain();
  o.frequency.setValueAtTime(300 * f, t);
  o.frequency.exponentialRampToValueAtTime(300 * f * (bend || 0.57), t + len);
  e.gain.setValueAtTime(0.0001, t);
  e.gain.exponentialRampToValueAtTime(0.5 * g, t + 0.002);
  e.gain.exponentialRampToValueAtTime(0.0001, t + len);
  o.connect(e); e.connect(out); o.start(t); o.stop(t + len + 0.02);
  if (!c) return;
  var n = ac.createBufferSource(), b = ac.createBiquadFilter(), ne = ac.createGain();
  n.buffer = noiseBuffer; b.type = 'bandpass'; b.frequency.value = 2600; b.Q.value = 0.9;
  ne.gain.setValueAtTime(0.24 * g * c, t); ne.gain.exponentialRampToValueAtTime(0.0001, t + 0.006);
  n.connect(b); b.connect(ne); ne.connect(out); n.start(t); n.stop(t + 0.02);
}
```

Give each kind of control its own voice, by what it is for. A large or weighty control sounds lower and longer, a small one higher and shorter, and the direction of the pitch follows the direction of the state.

| The control | f | d | c | g | Notes |
|---|---|---|---|---|---|
| Primary action | 0.62 | 1.6 | 0.8 | 1 | the one button that matters |
| Ordinary key | 1 | 1 | 1 | 0.85 | |
| Small choice (chip, radio, day, digit) | 1.5 | 0.65 | 1 | 0.7 | |
| A position (dial, segments, ruler) | 1.2 | 0.6 | 1.6 | 0.8 | pitch follows the position, one octave across the range |
| A step while dragging | 1.75 | 0.25 | 1.3 | 0.4 | pitch follows the value; at most one every 22 ms |
| Something that opens | 0.8 | 1.5 | 0.3 | 0.6 | |
| Switch on / off | 0.8 / 1.1 | 0.9 | 1.4 | 0.9 | bend 1.45 for on (rises), 0.55 for off (falls) |
| Confirmed | 1, then 1.5 | 1.3, 1.6 | 0.6 | 0.85 | two knocks, 110 ms apart |
| Refused | 0.5 | 0.8 | 0 | 0.8 | three knocks, 75 ms apart, no click |
