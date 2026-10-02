# Python-Series03

Group assignment for the IEAP Python course (SA1M118), University of Montpellier.
We find the zero crossings and the local maxima / minima of a sampled signal, use them to measure its
frequency, and study how white noise breaks the measurement and how a low-pass filter fixes it.

*Authors: Albatoul AHMAD, Valentin BALBINE, Chloé GILLES*

## Repository content

| File | Description |
|---|---|
| `Python-Series03.ipynb` | The notebook with all the code and explanations (main deliverable) |
| `README.md` | This file: presentation of the project, results and teamwork |
| `LICENSE` | MIT license |
| `.gitattributes` | Git configuration file (created with the repository) |

## Installation and use

```bash
git clone <URL of this repository>
cd <repository folder>
pip install numpy matplotlib scipy jupyter
jupyter notebook Python-Series03.ipynb      # then: Kernel > Restart & Run All
```

## What the notebook does

1. **Remarkable points of a simple signal**: positive / negative zero crossings and local extrema, with plotting functions.
2. **Known signal**: sum of a 2 Hz sine (amplitude 1) and a 1 Hz sine (amplitude 2, phase π/3), sampled at 100 Hz for 2 s.
3. **Frequency from zero crossings**: spacing between same-slope crossings gives the period.
4. **Noisy signal**: white noise added, remarkable points recomputed, then a Butterworth low-pass filter (5 Hz, `filtfilt`).

### Main functions

| Function | Role |
|---|---|
| `plot_zero_crossings(signal)` | Plots positive / negative zero crossings on the current figure |
| `plot_local_extrema(signal)` | Plots local maxima and minima on the current figure |
| `find_zero_crossings(signal)` | Returns the indices of the positive and negative crossings |
| `compute_frequency_from_zero_crossings(time, signal)` | Returns a dictionary with spacings, periods and frequency |
| `print_frequency_info(info)` | Prints that dictionary |
| `display_remarkable_points(sig, title, label, clean)` | Plots a signal with all its remarkable points |

## Main results

| Signal | Spacing between crossings (samples) | Frequency |
|---|---|---|
| Clean | 100 / 100 | **1.0 Hz** (expected) |
| Noisy (noise = 5 % of peak-to-peak) | `[60 100]` / `[3 97]` | 1.54 Hz (wrong) |
| Noisy, low-pass filtered at 5 Hz | `[101]` / `[99]` | **1.0 Hz** |

Over 300 noise realisations, the unfiltered estimate is correct in only 19 % of cases at 5 % noise, against 100 % after filtering.

> The exact noisy numbers differ from the assignment's example because the noise is random.

## Teamwork

- Each member worked on a personal branch and opened a pull request to `main`, reviewed by another member before merging.
- `main` always contains the last working version of the notebook.
- The contribution of each member is visible in the commit history (`git log --author`).

## License

Released under the [MIT License](LICENSE).
