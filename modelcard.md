# Model Card: Seed Viability Nomograph

## Model details

### Model name
Seed Viability Nomograph

### Model type
Deterministic scientific calculator implemented as a web application

### Version
Version 1.0, initial public web deployment

### Framework
React + Vite front end with browser-side numerical computation

## Model summary

This application estimates predicted seed viability under user-defined storage conditions using an Ellis-Roberts style viability framework. It accepts moisture content, temperature, storage duration, and viability constants, and returns predicted percentage viability, threshold times, a viability decline curve, and a digital nomograph table.

This is not a machine learning model. It is a rule-based quantitative implementation of a classical seed storage equation.

## Intended users

- seed scientists
- plant genetic resource curators
- crop science students
- agricultural educators
- restoration practitioners
- researchers exploring storage scenarios

## Intended uses

- teaching seed longevity principles
- prototyping storage scenarios
- visualizing effects of moisture and temperature on viability
- planning experimental design
- demonstrating the structure of viability-equation reasoning

## Out-of-scope uses

- clinical or medical applications
- authoritative genebank decisions without experimental calibration
- prediction for species lacking appropriate fitted constants
- decision support for recalcitrant seeds without specialist validation
- regulatory or legal decision making

## Inputs

Primary inputs:
- moisture content, percent
- storage temperature, degrees Celsius
- storage duration, days
- K?
- K?
- C?
- C?
- C?

Profile input:
- illustrative preset choice or custom parameter entry

## Outputs

- predicted viability, percent
- sigma, days
- time to 85% viability
- time to 75% viability
- P50, time to 50% viability
- time to 20% viability
- viability decline curve across time
- digital nomograph table across moisture values
- downloadable CSV

## Methodological basis

The application uses:

log??(?) = K? ? C?log??(m) ? C?t ? C?t?

v = K? ? p/?

p = (K? ? v)?

? = standard deviation of seed deaths in time, or storage-life parameter
v = viability after storage, expressed in probit units
K? = initial viability, in probit units
p = storage period
m = seed moisture content, in percent
t = storage temperature, in degrees Celsius
K? = species or seed-lot constant related to baseline longevity
C? = moisture sensitivity constant
C? = linear temperature constant
C? = quadratic temperature constant
t? = squared temperature term, used to capture the non-linear effect of temperature on longevity

and a probit-style viability decline relationship based on initial viability and elapsed storage time.

The app converts between viability percentage and a probit representation using numerical approximations to the normal cumulative distribution and its inverse.

Because the equation is expressed in log?? form, relatively small changes in moisture or temperature can produce large differences in ?, which is consistent with the well-established observation that orthodox seed longevity is highly sensitive to drying state and storage temperature (Ellis & Roberts, 1980; Ellis, Hong, & Roberts, 2006).

## Assumptions

- the chosen constants are biologically appropriate for the species or seed lot
- the seed lot behaves sufficiently like an orthodox storage system
- moisture and temperature are meaningfully represented by the selected values
- initial viability can be reasonably encoded in the chosen K? value

## Strengths

- transparent and interpretable
- fast browser-side execution
- accessible for non-specialists
- useful for education and exploratory modeling
- portable across desktop and mobile browsers

## Limitations

- illustrative presets are not experimentally fitted
- prediction quality depends heavily on constant quality
- non-orthodox seeds may not conform to the underlying framework
- no uncertainty intervals are currently presented
- no automatic calibration from observed germination data
- not validated as a decision-grade operational seed bank platform

## Ethical and scientific considerations

The app should be presented honestly as a scientific approximation and teaching tool unless supplied with experimentally fitted constants. Users should avoid overstating predictive certainty, particularly for species with intermediate or recalcitrant storage behavior.

## Maintenance recommendations

- document any constant changes
- validate species-specific presets against published or experimental data
- version outputs when updating equations or constants
- add unit tests for viability and sigma calculations
- retain transparency about intended and non-intended uses

