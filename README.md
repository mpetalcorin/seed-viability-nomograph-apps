# seed-viability-nomograph-apps
https://seed-viability-nomograph.vercel.app

A React and Vite web application for exploring seed longevity using a digital seed viability nomograph based on Ellis-Roberts style constants.
<img width="1227" height="535" alt="Screenshot 2026-04-14 at 02 18 39" src="https://github.com/user-attachments/assets/98806eab-2699-4ec0-b429-de4f246382f0" />
# Seed Viability Nomograph
A React and Vite web application for exploring seed longevity using a digital seed viability nomograph based on Ellis-Roberts style constants.

## Overview

This project provides an interactive browser-based tool for estimating predicted seed viability as a function of storage moisture content, storage temperature, storage duration, and seed viability constants. The app is designed mainly for teaching, demonstration, and research prototyping in orthodox seed storage contexts.

The interface allows users to:
- adjust moisture content, temperature, and storage duration
- select illustrative preset profiles
- enter custom constants
- view predicted viability decline over time
- estimate time to threshold viability values such as 85%, 75%, 50%, and 20%
- export a moisture-sweep nomograph table as CSV

## Scientific basis

The application implements an Ellis–Roberts style viability framework in which the spread of seed deaths in time is represented by σ and longevity is linked to both seed moisture content and storage temperature. In the software, the storage-life parameter is estimated from the classical relationship: 

log₁₀(σ) = Kᴱ − Cᵂlog₁₀(m) − Cᴴt − Cᑫt²

v = Kᵢ − p/σ

p = (Kᵢ − v)σ

where 
- σ = standard deviation of seed deaths in time, or storage-life parameter
- v = viability after storage, expressed in probit units
- Kᵢ = initial viability, in probit units
- p = storage period
- m = seed moisture content, in percent
- t = storage temperature, in degrees Celsius
- Kᴱ = species or seed-lot constant related to baseline longevity
- Cᵂ = moisture sensitivity constant
- Cᴴ = linear temperature constant
- Cᑫ = quadratic temperature constant
- t² = squared temperature term, used to capture the non-linear effect of temperature on longevity
- Kᴱ, Cᵂ, Cᴴ, and Cᑫ are constants supplied either through presets or by manual user entry (Ellis & Roberts, 1980; Ellis, Hong, & Roberts, 2006).

Predicted viability after a storage period p is derived in probit space as v = Kᵢ − p/σ, where Kᵢ denotes initial viability in probit units. 

Viability decline is projected using a probit-based deterioration model and converted to percentage viability for display.

The browser application converts between probit values and percentage germination using a normal cumulative distribution transform and its inverse, enabling the outputs to remain intuitive for non-specialist users while retaining the structure of the underlying longevity model.

## Intended use

This tool is intended for:
- teaching seed longevity concepts
- demonstrating the effect of moisture and temperature on storage life
- exploratory modeling
- rapid prototyping before experimental fitting

This tool is not intended to replace species-specific laboratory calibration, long-term storage trials, or formal genebank decision workflows.

## Current features

- interactive controls for moisture, temperature, and storage duration
- preset profiles for illustrative seed-lot behaviors
- custom constant editing
- viability decline curve
- threshold time summaries
- digital nomograph table
- CSV export

## Project structure

- `src/App.jsx` contains the main interface and computational logic
- `src/components/ui/` contains lightweight UI wrapper components
- `src/index.css` contains Tailwind-based styling
- `tailwind.config.js` and `postcss.config.js` support styling setup
- `vite.config.js` defines the Vite build configuration

## Installation

Clone the repository and install dependencies:

```bash
npm install
```

Run locally:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

## Deployment

This project is suitable for deployment on Vercel from a GitHub repository. After deployment, the app can be used in desktop and mobile browsers, including Safari on iPhone and Chrome on Android.

## Important limitations

The preset constants in the current version are illustrative. They should not be treated as authoritative species constants. Output quality depends on the biological realism of the chosen parameters. The classical viability framework is most appropriate for orthodox seeds and should be interpreted cautiously for intermediate or recalcitrant materials.

## Suggested future improvements

- species-specific fitted constant libraries
- relative humidity and equilibrium moisture conversions
- upload of germination datasets for fitting constants
- warnings for biological ranges beyond safe storage windows
- more advanced support for intermediate and recalcitrant seed scenarios

## Citation
**Petalcorin, M.I.R.** (2026). A web-based digital seed viability nomograph for interactive estimation of seed longevity from moisture content, temperature, and storage duration. https://github.com/mpetalcorin/seed-viability-nomograph-apps

