# Tidal - Kindohm videos

## Workflow from scratch: TidalCycles sequencing and Harmor + RYTM sound design
[Video link](https://www.youtube.com/watch?v=eGdL4d7_Uw4&t=1980s)

### General things picked up from this video
Define a function to manipulate a pattern (this is why definitions you were doing previously were not working in some cases)...
```
let limit p = (|* gain 1.2) $ p
d1 $ limit $ s "bd" # n 0
``` 
The function `limit` expects a pattern as it's argument. Not entirely sure what the `|*`syntax is. But it must mean, apply to all...?

This syntax is interesting
```
{0@7 1@3 0@6 2*13}%16
```
The `@` I know and makes things sustain for x amount of time. Wrapping the pattern in `{}%16` is for `Polymetric sequence subdivision` see [here](https://tidalcycles.org/index.php/Mini_notation_syntax)

`rand` used in the same pattern will output the same values. If you want two `rand`s, or any other random generator to output different values you'll need to move it on somehow. A nice helper function is:
```
shrand x = (x ~>) $ rand
```
Which offsets rand by the desired value

`binary` allows you to express a boolean pattern as a decimal number! interesting! For example, you could write:
```
d1 $ struct "t f t f f f t t" $ sound "clap:4"
```
as
```
d1 $ struct (binary 163) $ sound "clap:4"
```

`sometimesBy` - make a helper function for it
```
sb = sometimesBy 
```

### Create a loose pattern map with fmap
Map a pattern of integers to patterns of different types. `fmap` is a Haskell function. 
```
let pat = "0 0 1 1 0 2 1 2"
d1 $ midichan ( fmap ([2,6,3]!!) $ pat )
    # s "drummachine"
```
So, this rather confusing syntax maps the 0s in `pat` to 2, the 1s to 6 and the 2s to 3. 

He ends up with something a bit like this
```
let pat = "0 0 1 1 0 2 1 2"
d1  $ limit 
    $ stack [
        midichan ( fmap ([2,6,3]!!) $ pat )
        , ccn 10 # ccv 12
        , ccn 10 # ccv 12
        , ccn 10 # ccv 12
        ...
    ]
    # s "drummachine"
```

Does some nice things with randomness.