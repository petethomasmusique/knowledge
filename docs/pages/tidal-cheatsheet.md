# Tidal Cheatsheet

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
