# Euler equations for ideal gas dynamics

The `Euler` object is in the `Eq` module, and can be loaded as

~~~~~~~ {.lua}
HyperEquation = require "Eq"
~~~~~~~

To construct the object, for example, do:

~~~~~~~ {.lua}
euler = HyperEquation.Euler { gasGamma = 1.4 }
~~~~~~~

where `gasGamma` is the gas adiabatic constant. The constructor takes
no other parameters.

The following methods are provided:

`euler:numEquations()`
: Number of equations in system. Is always 5.

`euler:numWaves()`
: Number of waves in system. Is always 3.

`euler:gasGamma()`
: Gas adiabatic constant.

`euler:flux(dir, qIn, fOut)`
: Compute the flux (output in `fOut`) along direction `dir` given the
  conserved variable `qIn`.

`euler:isPositive(q)`
: Checks if density and pressure are positive, returning `true` if
  they are, false otherwise.

`euler:rp(dir, delta, ql, qr, waves, s)`
: Computes the `waves` and speed `s` given the jump `delta`. Shape of
  `waves` matrix is (mwave X meqn).

`euler:qFluctuations(dir, ql, qr, waves, s, amdq, apdq)`
: Computes the q-fluctuations, given waves and wave speeds. The
  fluctuations in normal cases are defined by $A\Delta Q^- =
  \sum_{s<0} s W$ and $A\Delta Q^+ = \sum_{s>0} s W$. Shape of `waves`
  matrix is (mwave X meqn).