# nnDMT CH Abort Dose Estimator

**A harm reduction modeling tool for vaporized N,N-dimethyltryptamine (nnDMT) used as an acute abortive treatment for cluster headache**

[![DOI](https://zenodo.org/badge/DOI/1302987762.svg)](https://doi.org/10.5281/zenodo.21399191)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Overview

This tool estimates bioavailable nnDMT (in milligrams) from user-reported vaporization parameters including device type, mixture concentration, inhalation technique, and thermal efficiency. This tool does NOT provide medical advice. It is designed to support:

- **Harm reduction education** for the cluster headache patient community
- **Survey instrument design** for community-based research into psychedelic CH treatment
- **Dose-response modeling** from self-reported data, in the tradition of the Clusterbusters Medication Use Survey (Schindler et al., 2015)
- **PS27 presentation support** — Psychedelic Science 2027, Denver

The calculator covers the full range of common community-reported delivery methods: 510-thread cartridges, pod systems (Vaporesso XROS, OXVA Xlim, etc.), e-rigs (Ispire Daab, Yocan Orbit, Puffco Peak Pro), direct e-mesh RDA (SS316L), sub-ohm tanks/RTAs, dedicated TC vaporizers, and glass pipe. More may be added in the future. 

---

## Live Calculator

**→ [Launch the calculator](https://CHARC-ORG.github.io/nndmt-ch-dose-estimator)**

---

## The Dose Model

Estimated bioavailable DMT (mg) is calculated as:

```
mg_bioavailable =
  (cart_volume_ml × concentration_mg_per_ml) ÷ puffs_per_cart
  × puffs_taken
  × temperature_efficiency_factor
  × carrier_factor
  × crystallization_factor
  × (puff_duration × inhalation_style_factor)
  × hold_retention_factor
  × puff_interval_factor
```

### Temperature Efficiency Model

Coil temperature is estimated from wattage using:

```
T_coil (°C) ≈ 80 + (W × 4.5)
```

For ceramic/pod coils at steady state. TC-mode and induction devices (Ispire Daab) use set temperature directly.

Efficiency factors reflect DMT preservation across the vaporization window:
- **<160°C**: Under-vaporization (0.33–0.72× base)
- **160–185°C**: Optimal window (base efficiency; ceramic ~0.90, quartz ~0.72)
- **185–215°C**: Upper range (0.89× base)
- **215–230°C**: Combustion begins (0.72× base)
- **>230°C**: Significant combustion (0.30–0.54× base)

### Inhalation Style Factors

| Style | Factor | Basis |
|---|---|---|
| Direct-to-lung (DTL) | 0.88 | ~500ml puff volume |
| Restricted DTL | 0.76 | Intermediate |
| Mouth-to-lung (MTL) | 0.65 | ~55ml puff volume |

*Based on published e-cigarette topography data (Behar et al., 2015; Prasad et al., 2022)*

### E-Mesh Special Case

For the direct e-mesh (freebase powder on SS316L mesh) method, the model bypasses the liquid concentration calculation entirely. Efficiency is based on community-reported data from the DMT-Nexus e-mesh thread, cross-referenced with TC-mode temperature set points.

---

## Uncertainty

Individual estimates carry ±30–40% uncertainty for liquid-based methods due to:
- Unknown actual coil temperature vs. estimated
- Concentration variability in unverified/pre-filled cartridges
- Inhalation volume variability between users
- Crystallization and wicking inconsistency

E-mesh estimates are tighter (±18%) due to direct measurement of loaded mass.

**This tool produces estimated ranges, not precise clinical doses.** It is a modeling instrument for harm reduction education and survey design, not a dosing guide.

---

## Device Database

Covered devices include:

**E-rigs / TC wax devices**
- Ispire Daab (induction, all-glass, 121–427°C — highest precision)
- Puffco Peak Pro, Focus V Carta 2, Dr. Dabber Switch
- Yocan Orbit (3 voltage settings modeled separately — only 3.4V/White is within DMT window)
- Yocan Evolve Plus

**510-thread carts**
- CCELL ceramic at multiple voltage settings
- Quartz and cotton wick variants

**Pod systems**
- Vaporesso XROS Pro, 4, 3, 2, 1
- OXVA Xlim SQ2, Pro, C
- Caliburn G3/A3S, VOOPOO Vinci 3, SMOK Nord 5

**Sub-ohm tanks / RTA**
- GeekVape Z2, Zeus, Hellvape Dead Rabbit V3 RTA, Vaporesso NRG, Freemax Mesh Pro
- DIY RDA (SS316L TC, ceramic, cotton)

**E-Mesh RDA**
- Wotofo Profile + VandyVape SS316L 150/200/400 mesh in TC-SS mode

**Dedicated TC vaporizers**
- Storz & Bickel Mighty, Volcano (set-temperature mode)

**Glass pipe + torch**
- Experience-level adjusted efficiency (0.28–0.45)

---

## Clinical Context

Cluster headache ("suicide headache") affects approximately 0.1% of the population with attacks rated at the extreme end of the pain scale (Kip 9–10). Community surveys (Schindler et al. 2015, 2022, 2024; Clusterbusters Medication Use Survey 2023) document widespread off-label use of tryptamine compounds including psilocybin and vaporized nnDMT, with the latter showing a 67.5% complete abort rate in interim data from the Yale/VA Connecticut DMT survey (Schindler, 2025).

This tool is part of a broader harm reduction and research advocacy project targeting PS27 (Psychedelic Science 2027) and supports collaborative work with Clusterbusters/ClusterInfo.org/ClusterBuds.

---

## Citation

If you use this tool in research, please cite:

```
[King Frey / CHARC]. (2026). nnDMT CH Abort Dose Estimator (v1.0.0). Zenodo. https://doi.org/PLACEHOLDER
```

## Feature / Device Requests

email wearecharc@gmail.com

See `CITATION.cff` for machine-readable citation metadata.

---

## References

- Schindler EAD et al. (2015). Indoleamine hallucinogens in cluster headache: Results of the Clusterbusters medication use survey. *Journal of Psychoactive Drugs*, 47(5), 372–381.
- Schindler EAD et al. (2022). Exploratory controlled study of the migraine-suppressing effects of psilocybin. *Neurotherapeutics*, 18(1), 534–543.
- Schindler EAD et al. (2024). Psilocybin for cluster headache: Blinded extension phase results. *Neurology*.
- Strassman RJ & Qualls CR (1994). Dose-response study of N,N-dimethyltryptamine in humans. *Archives of General Psychiatry*, 51(2), 85–97.
- Good MA et al. (2023). Pharmacokinetics of N,N-dimethyltryptamine in humans. *Clinical Pharmacokinetics*.
- Behar RZ et al. (2015). Development, validation and application of a device to measure e-cigarette users' puffing topography. *Nicotine & Tobacco Research*.

---

## Disclaimer

This tool is for harm reduction education and research survey design only. It does not constitute medical advice. DMT is a Schedule I controlled substance in the United States and regulated or prohibited in most jurisdictions. Nothing in this tool facilitates illegal activity.

The developer has lived experience with cluster headache and PTSD as a USMC combat veteran. This project is motivated by advocacy for a patient population that has been inadequately served by conventional medicine.

---

## License

MIT License — see `LICENSE`
