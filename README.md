# Cable
A fretted instrument chord generator written in Python

Create a new instance of Cable, optionally specifying a tuning and maximum number of spanned frets
```
from Cable import Cable, STANDARD, Note, Interval, Quality, Extension
cable = Cable.Cable(tuning=STANDARD, span=3)
```

Build chords by specifying the note and optionally added notes, bass, quality, and extension
```
# Bb major:
cable.generate(Note.Bb)

# Building chords:

# F# Power chord
cable.generate(Note.Fs, Interval.PERFECT_FIFTH, Interval.PERFECT_FOURTH)
# The above can also be written as:
cable.generate(Note.Fs, Interval.a4, Interval.a5)

# A#maj#11 chord
cable.generate(Note.As, # Sharp/flat notes are succeded by s or b
               Interval.M7,  # capital M for a major 3rd, 7th, or 6th. Lowercase m for minor
               Interval.a9,  # Standard added intervals are preceded by the letter 'a'
               Interval.s11, # Sharp/flat intervals are preceded by s or b
               quality=Quality.MAJ)
# Can also be written as:
cable.generate(Note.As,
               quality=Quality.MAJ,
               extension=Extension.s11)  # Sharp/flat extensions are preceded by s/b

# Bb9/F# chord:
cable.generate(Note.Bb,
               bass=Note.Fs,
               extension=Extension.E9)  # Unmodified extensions are preceded by E
```

Create a new tuning of any length by creating a list of notes:
```
BASS_DROP_D = [Note.D, Note.A, Note.D, Note.G]
cable = Cable(tuning=BASS_DROP_D)
```