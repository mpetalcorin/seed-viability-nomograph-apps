# Datasheet: Seed Viability Nomograph Project

## Motivation

### Why was this project created?
This project was created to translate a classical seed viability nomograph into an accessible digital web interface. The aim is to make seed longevity concepts easier to explore, teach, and communicate using modern browser-based tools.

### What real-world need does it address?
Many students, seed scientists, and conservation users understand the importance of moisture and temperature in seed storage, but classical nomographs and equations can be difficult to interpret quickly. This project addresses the need for an interactive digital implementation that is easy to test on desktop and mobile devices.

## Composition

### What does the project contain?
The repository contains:
- a React and Vite web application
- browser-side numerical functions for viability estimation
- lightweight UI component wrappers
- styling configuration and build files
- CSV export capability for nomograph tables

### What does it not contain?
It does not currently include:
- experimentally fitted species-specific constant libraries
- uncertainty models
- backend services
- user accounts
- uploaded experimental datasets
- automated calibration workflows

## Data and parameters

### What data are used?
The current public version mainly uses user-supplied values and built-in illustrative presets. No external live database is required for core app operation.

### Are built-in constants authoritative?
No. The built-in presets are illustrative and should be replaced with fitted constants for real species-specific or lot-specific work.

## Collection process

### How were defaults chosen?
The defaults were selected as concept-demonstration values to show how the interface behaves under different longevity profiles. They are not presented as a validated reference library.

## Preprocessing and transformations

### What transformations are performed?
- percentage viability is transformed to and from a probit-like representation
- sigma is calculated from moisture and temperature using an Ellis-Roberts style equation
- threshold times are calculated from sigma and target viability values
- curve and table outputs are derived from repeated deterministic calculations

## Uses

### What are appropriate uses?
- classroom teaching
- conceptual demonstrations
- seed longevity visualization
- preliminary exploration of storage scenarios
- software prototyping
- outreach and communication

### What are inappropriate uses?
- decision-grade seed bank operations without validation
- species conservation planning without fitted constants
- prediction for recalcitrant seeds without specialist review
- claims of validated forecasting accuracy where no calibration exists

## Distribution

### How is the project shared?
The app is shared as source code in a GitHub repository and is deployed as a web application through Vercel.

### On what devices can it run?
The deployed application can be used on desktop browsers and mobile browsers, including iPhone and Android devices.

## Maintenance

### Who should maintain it?
The maintainer should be someone comfortable with seed biology, JavaScript or React-based web development, and the scientific context of viability equations.

### What should future maintenance include?
- updating documentation
- replacing illustrative presets with validated constants where available
- checking browser compatibility
- improving accessibility and mobile behavior
- documenting version changes
- adding tests for core numerical functions

## Risks and cautions

### What are the main scientific risks?
The main risk is overinterpreting outputs from illustrative constants or from biologically inappropriate use cases. The app reflects a classical framework that is strongest in orthodox seed storage contexts.

### What are the main software risks?
Potential risks include incorrect user inputs, misunderstood units, missing validation for extreme values, and future dependency changes in the front-end stack.

## Summary statement

This project is a transparent, browser-based digital seed viability nomograph intended primarily for teaching, exploration, and prototyping. It becomes more useful scientifically when paired with carefully fitted constants and explicit biological context.
