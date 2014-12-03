Scribbletune (WIP)
------------------

Generate musical patterns with JavaScript and export as MIDI files using node.js

### Install

`npm install scribbletune`

### Generate

You can `require` the scribbletune module and use it to generate modes and patterns to create melodies. For example, to create a 16 beat simple bass line comprising of the first 3 notes of the C phrygian mode on the second octave, you could create a new file and add some code like this:

```
var scribble = require('scribbletune');

var clip = scribble.clip({
    notes: scribble.mode('c', 'phrygian', 2).slice(0, 3),
	pattern: '-xxx-xxx-xxx-xxx',
	sizzle: true
});

scribble.render(clip, 'bass.mid');
```
This will create a MIDI file called bass.mid in the same location as the above file.

### Binary

You can use the scribbletune binary to create tunes as well. To generate a Midi file with the C Major scale using the binary:

`./node_modules/scribbletune/bin/scribbletune`

Generate a MIDI file with the C Phrygian mode in the second octave

`./node_modules/scribbletune/bin/scribbletune --root c --octave 2 --mode phrygian`

Generate a MIDI file with the pattern: x---x---x___x--- (note the 'equal to' sign - This is to allow for patterns that start with hyphens)

`./node_modules/scribbletune/bin/scribbletune --pattern=x---x---x___x---`


### Patterns

Patterns are denoted by a string made up of x, - and \_ where `x` stands for noteOn, `-` stand for noteOff and `_` stands for sustain. Patterns can be used to create sizzle maps (which are basically accent maps to hit some notes harder than others)

### Note

You will need an application like Ableton Live or Reason or Garage Band to use the generated MIDI file. The file will be generated in the same directory as `music.mid`
