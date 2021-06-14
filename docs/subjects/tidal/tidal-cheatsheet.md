# Tidal Cheatsheet

## Mini notation
`?` randomly decides whether an event should play:  
```
"bd hh? sd hh?"
```

Adding a decimal (e.g. `?0.5`) sets the likelihood of an event playing, in this case a 50/50 chance.

`|` separates sequences, like `,`, but rather than layering them up, it chooses one of them to play each cycle:
```
d1 $ s "bd [mt|ht lt ht]
```
## Functions
[qtrigger](https://tidalcycles.org/qtrigger)  
Start and trigger patterns from the start, quantized with next cycle:
```
d1 $ qtrigger 1 $ n "c d e f" # sound "superpiano"
```

[trigger](https://tidalcycles.org/trigger)  
Reset pattern
```
d1 $ sound "bd*2 cp:4(5,8,<0 2>)"
  # gain (trigger 1 $ slow 2 envL)
```
