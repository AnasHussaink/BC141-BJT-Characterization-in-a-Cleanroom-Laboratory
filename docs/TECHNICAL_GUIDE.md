# Technical revision guide

[Project README](../README.md)

## What the practical work means

You investigated an existing semiconductor device electrically. Probe alignment/contacting and BJT curve measurements are confirmed personal tasks, and BC141 is a confirmed tested device. The physical activity is device characterization, with cleanroom experience as its laboratory context.

Characterization asks how a device behaves under a defined stimulus. Fabrication concerns making or modifying the device through processes such as deposition, lithography and etching. The available evidence supports the characterization activity.

## Equipment roles

The station holds the sample/fixture while the micropositioners move contacts. The microscope provides the visual feedback needed to place the probes. The analyzer applies controlled electrical conditions and measures responses. EasyEXPERT provides the visible test-management and plotting interface.

A source-measure unit can source a voltage while measuring current, or source current while measuring voltage, within its configuration and limits. The installed module configuration, channel assignments, bias limits and compliance settings must come from the actual session records. The B1500A product's available capabilities are not evidence that all such modes were used in this lab. [Keysight product reference](https://www.keysight.com/us/en/product/B1500A/semiconductor-device-parameter-analyzer-system-mainframe.html).

The photograph shows probes around a PCB-mounted device fixture. It does not establish wafer fabrication or wafer-level yield testing. MPI's exact station model should be recorded from its label or the lab equipment list before naming a model on a CV.

## BJT concepts

A bipolar junction transistor has emitter, base and collector terminals. Its characteristic curves relate terminal currents to terminal voltages under defined bias conditions.

For the usual forward-active NPN convention, base and collector currents flow into the device and emitter current flows out, so `I_E = I_C + I_B`. An analyzer may use a different terminal-current sign convention; record it before calculating ratios or plotting logarithms.

The key operating regions are cutoff, forward active, saturation, and reverse active. A curve's slope or bend alone does not identify a region without knowing the applied terminal voltages and the measurement limits.

## Common emitter and common base

In common-emitter measurements, the emitter is the common terminal. Input behavior is often expressed as base current versus base-emitter voltage, while output behavior relates collector current to collector-emitter voltage at a controlled base condition.

In common-base measurements, the base is the common terminal. The experiment examines emitter input and collector output behavior with the appropriate collector-base voltage convention.

Record which terminal is held, which voltage/current is swept, and which quantity labels each curve. The course includes both configurations; the actual completed dataset list still needs to be recovered.

## Quantities that can be extracted from suitable data

| Quantity | Definition under stated bias conditions | Required evidence |
|---|---|---|
| DC common-emitter gain | `beta_DC = I_C / I_B` | Corresponding collector/base currents at the same operating point |
| DC common-base gain | `alpha_DC = I_C / I_E` using consistent current magnitudes/signs | Corresponding collector/emitter currents |
| Differential input resistance | `r_in = dV_BE / dI_B` at fixed `V_CE` | Input curve and a documented local fitting interval |
| Differential output resistance | `r_out = dV_CE / dI_C` at fixed `I_B` | Forward-active output curve with valid bias control |
| Voltage feedback coefficient | `dV_BE / dV_CE` at fixed `I_B` | Appropriate paired/interpolated bias points |
| Early intercept | Fit `I_C = m V_CE + c`; x-intercept is `-c/m` | A justified forward-active interval, units, and fit diagnostics |

The magnitude of the negative x-intercept is often reported as a positive Early voltage. State the sign convention. Do not mix a voltage-swept output curve at fixed base voltage with a fixed-base-current resistance definition without explaining the difference.

DC gain is a current ratio; small-signal gain is a local derivative. They need not be identical. Extremely small denominator currents make gain ratios unreliable, so checks for noise floor, leakage, compliance and missing values are part of the analysis.

## Gummel plots

A Gummel plot presents base and collector currents against base-emitter voltage on an appropriate logarithmic current scale, under a defined additional bias condition. It helps compare current behavior over multiple orders of magnitude. Keysight's application library includes BJT Gummel tests and gain extraction. [EasyEXPERT application reference](https://www.keysight.com/zz/en/assets/9018-01852/reference-guides/9018-01852.pdf).

The existence of that test in a handout or software library does not establish that the corresponding export is present. Zero or negative signed values cannot simply be placed on a logarithmic axis; document any magnitude convention and exclusions.

## Early effect

Base-width modulation contributes to a nonzero slope in the forward-active output characteristic. A local linear fit can estimate output conductance/resistance and an extrapolated intercept. Saturation, self-heating, compliance and breakdown regions must not be silently included in that fit.

A result should include the bias condition, fitting range and uncertainty or fit quality. A photograph of a plot is not enough to report a reliable numeric Early voltage.

## Switching and lifetime

The course includes a switching exercise intended to estimate minority-carrier lifetime. Completion of this exercise is not yet confirmed. It requires a time-domain trace and the applicable circuit/model assumptions.

Do not directly substitute a 10–90% rise time into a zero-to-threshold formula: the measured interval and the model interval must match. For any future extraction, record the drive waveform, load, base drive, timing definition, equipment bandwidth and the assumptions behind the calculation.

## What to inspect in the recovered data

Preserve the original files before conversion. Confirm device ID, terminal mapping, units, sweep directions, stepping parameters, compliance/status flags and temperature. Separate valid measurements from incomplete sweeps and contacts that were being adjusted. A flat segment can reflect a compliance limit rather than intrinsic device behavior.

Use the original instrument setup/report to interpret the plotted photograph. No quantitative BC141 result has been inferred from that photograph in this repository.
