# Strudel CheatSheet

https://strudel.cc/workshop/recap/

## Mini Notation

| Concept          | Syntax  | Example                            |
| ---------------- | ------- | ---------------------------------- |
| Sequence         | `space` | `sound("bd bd sn hh")`             |
| Sample Number    | `:x`    | `sound("hh:0 hh:1 hh:2 hh:3")`     |
| Rests            | `~`     | `sound("metal ~ jazz jazz:1")`     |
| Sub-Sequence     | `[]`    | `sound("bd wind [metal jazz] hh")` |
| Sub-Sub-Sequence | `[[]]`  | `sound("bd [metal [jazz sn]]")`    |
| Speed Up         | `*`     | `sound("bd sn*2 cp*3")`            |
| Slow Down        | `/`     | `note("[c a f e]/2")`              |
| Parallel         | `,`     | `sound("bd*2, hh*2 [hh oh]")`      |
| Alternate        | `<>`    | `note("c <e g>")`                  |
| Elongate         | `@`     | `note("c@3 e")`                    |
| Replicate        | `!`     | `note("c!3 e")`                    |

## Sounds

| Name  | Description                       | Example                              |
| ----- | --------------------------------- | ------------------------------------ |
| sound | plays the sound of the given name | `sound("bd sd")`                     |
| bank  | selects the sound bank            | `sound("bd sd").bank("RolandTR909")` |
| n     | select sample number              | `n("0 1 4 2").sound("jazz")`         |

## Notes

| Name       | Description                   | Example                                                                          |
| ---------- | ----------------------------- | ---------------------------------------------- |
| note       | set pitch as number or letter | `note("b g e c").sound("piano")`               |
| n + scale  | set note in scale             | `n("6 4 2 0").scale("C:minor").sound("piano")` |
| $: (stack) | play patterns in parallel     | `$: s("bd sd")`                                |

## Audio Effects

| Name  | Example                                             |
| ----- | --------------------------------------------------- |
| lpf   | `note("c2 c3").s("sawtooth").lpf("<400 2000>")`     |
| vowel | `note("c3 eb3 g3").s("sawtooth").vowel("<a e i o>")`|
| gain  | `s("hh*8").gain("[.25 1]*2")`                       |
| delay | `s("bd rim").delay(.5)`                             |
| room  | `s("bd rim").room(.5)`                              |
| pan   | `s("bd rim").pan("0 1")`                            |
| speed | `s("bd rim").speed("<1 2 -1 -2>")`                  |
| range | `s("hh*16").lpf(saw.range(200,4000))`               |

## Pattern Effects

| Name   | Description                         | Example                                         |
| ------ | ----------------------------------- | ----------------------------------------------- |
| setcpm | sets the tempo in cycles per minute | `setcpm(90) /*default: 30 (120/4 bpm)*/`        |
| fast   | speed up                            | `sound("bd sd").fast(2)`                        |
| slow   | speed down                          | `sound("bd sd").slow(2)`                        |
| rev    | reverse                             | `n("0 2 4 6").scale("C:minor").rev()`           |
| jux    | split left/right, modify right      | `n("0 2 4 6").scale("C:minor").jux(rev)`        |
| add    | add numbers / notes                 | `n("0 2 4 6".add("<0 1 2 1>")).scale("C:minor")`|
| ply    | speed up each event n times         | `s("bd sd").ply("<1 2 3>")`                     |
| off    | copy, shift time & modify           | `s("bd sd, hh*4").off(1/8, x=>x.speed(2))`      |

## Drumkit

| Abbreviation | Drum                 |
| --------     | -------------------- |
| **bd**       | Bass drum, Kick drum |
| **sd**       | Snare drum           |
| **rim**      | Rimshot              |
| **cp**       | Clap                 |
| **hh**       | Closed hi-hat        |
| **oh**       | Open hi-hat          |
| **cr**       | Crash                |
| **rd**       | Ride                 |
| **ht**       | High tom             |
| **mt**       | Medium tom           |
| **lt**       | Low tom              |
|              |                      |
| **sh**   | Shakers (and maracas, cabasas, etc) |
| **cb**   | Cowbell                             |
| **tb**   | Tambourine                          |
| **perc** | Other percussions                   |
| **misc** | Miscellaneous samples               |
| **fx**   | Effects                             |


## Genres

Basic rock beat
```javascript
setcpm(100/4)
sound("[bd sd]*2, hh*8").bank("RolandTR505")
```

Classic House
```javascript
sound("bd*4, [- cp]*2, [- hh]*4").bank("RolandTR909")
```

Basic rock beat
```javascript
setcpm(81/2)
sound("bd*2 cp").bank("RolandTR707")
```

