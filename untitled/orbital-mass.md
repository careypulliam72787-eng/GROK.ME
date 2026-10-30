---
description: Calculate a body's mass from an orbit.
---

# Orbital mass

## Orbital mass

Use an object's orbit to estimate the mass it encloses. This method works when gravity dominates the motion.

### Circular orbits

For a circular orbit, calculate the enclosed mass with:

$$
M = \frac{4\pi^2 r^3}{G T^2}
$$

* $M$ is the enclosed mass.
* $r$ is the orbital radius from the central body's center.
* $T$ is the orbital period.
* $G$ is the gravitational constant.

Use SI units: metres for $r$, seconds for $T$, and $G = 6.67430 \times 10^{-11}\ \mathrm{m^3,kg^{-1},s^{-2\}}$. The result is in kilograms.

{% hint style="info" %}
Measure $r$ from the central body's centre, not its surface. Add the body's radius to an altitude measurement.
{% endhint %}

### Elliptical orbits

For an elliptical orbit, replace $r$ with the semi-major axis $a$:

$$
M = \frac{4\pi^2 a^3}{G T^2}
$$

This gives the combined mass of both orbiting bodies. When one body is much smaller, it closely approximates the central body's mass.

### When results look wrong

Check these common issues:

* Convert periods to seconds before calculating.
* Use the semi-major axis, not the closest orbital distance.
* Account for both bodies when their masses are comparable.

The estimate assumes a two-body system. Nearby objects and non-gravitational forces can affect the orbit.
