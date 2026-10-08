# strcs

Flexible parametric survival models on the log hazard scale, in Stata.

`strcs` models the baseline log hazard with restricted cubic splines and integrates the hazard numerically, by Gauss-Legendre quadrature, to obtain the likelihood.

## What it fits

- **Baseline:** restricted cubic splines of log time, or of time, with knots placed by degrees of freedom or given by the user.
- **Time-dependent effects:** each with its own spline function.
- **Relative survival:** through an expected mortality rate.
- **Data:** single- or multiple-record and single- or multiple-failure `st` data; weights are taken from `stset`.
- **Predictions:** hazard, survival and cumulative hazard functions, time-dependent hazard ratios, and differences in hazard and in survival, with confidence intervals.

## Requirements

- Stata 13.1 or later
- `rcsgen`: `ssc install rcsgen`

## Installation

The current stable version of `strcs` can be installed from the SSC archive by typing:

```stata
ssc install strcs
```

To install directly from this GitHub repository, use:

```stata
net install strcs, from("https://raw.githubusercontent.com/mjcrowther/strcs/main/")
```

## Example

A proportional hazards model with 4 degrees of freedom for the baseline, then the same model with a time-dependent effect of treatment:

```stata
webuse brcancer, clear
stset rectime, failure(censrec = 1)
strcs hormon, df(4)
strcs hormon, df(4) tvc(hormon) dftvc(3)
```

Further examples are in the help file: `help strcs`.

## Version

Version 1.85 (21 November 2018), the same version as on SSC.

## References

> Bower H, Crowther MJ and Lambert PC. strcs: A command for fitting flexible parametric survival models on the log-hazard scale. *The Stata Journal* 2016;16(4):989-1012.

## Licence

Copyright (C) 2015-2018 Hannah Bower, Michael J. Crowther and Paul C. Lambert.

Released under the GNU General Public License, version 3. See [`LICENSE`](LICENSE).
