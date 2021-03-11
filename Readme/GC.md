# GC

GC means Garbled Circuit.

## Garbled circuits Scheme

- A garbling scheme G consists of for PT algorithms (Gb, En, Ev, De):
  - Gb$(1^\lambda , f)$ → (F, e, d)
    - 1^λ is the security parameter and f is a circuit , and return a garbled circuit $F$
  - En$(e,x)$ → $X$
    - Takes in the encoding information e and an input x, return a garbled input $X$
  - Ev$(F, X)$ → $Y$
    - Takes in the garbled circuit F and the input X and return garbled output $Y$
  - De$(d, Y) $→$ y$
    - Takes in the decoding information d and the output Y and return the plaintext output $y$