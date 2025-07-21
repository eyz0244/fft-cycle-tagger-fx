# fft-cycle-tagger-fx

Extracts dominant cycle length and power using a rolling FFT on daily FX returns.  
Designed for fast signal tagging, spectral inspection, and regime diagnostics.

---

## Overview

For each of the 7 major currency pairs, this tool:

- Computes 256-day rolling FFT on daily log returns
- Identifies the dominant frequency (ignoring DC)
- Converts that frequency to **cycle length** (days per cycle)
- Computes **power** of that dominant frequency (magnitude squared)
- Outputs a clean `.csv` tag file: `date, pair, cycle_length, cycle_power`

---

## Assets Covered

- EURUSD  
- USDJPY  
- GBPUSD  
- USDCHF  
- AUDUSD  
- USDCAD  
- NZDUSD

---

## Output Files

### `data/fft_cycle_tags.csv`

| date       | pair    | cycle_length | cycle_power |
|------------|---------|---------------|--------------|
| 2010-01-04 | EURUSD | 14.67         | 0.0318       |
| ...        | ...     | ...           | ...          |

Each row represents a window-ending timestamp with the most dominant detected cycle.

---

## Key Visuals (`plots/`)

- `fx_{pair}_fft_cycle_and_power_chart.png`: dual-panel view per pair
- `fft_dominant_cycle_length_grid.png`: cycle-length comparison across all pairs
- `fft_cycle_power_grid.png`: power comparison grid
- `power_vs_cycle_length_scatter.png`: structure of spectral regimes across all pairs

---

## Interpretation

- **Short cycles (2–10 days)** dominate most of the post-2010 period.
- **High cycle power** is rare and typically tied to macro regime shifts (e.g., 2008, 2020).
- Structural differences are visible:
  - NZDUSD, AUDUSD exhibit more persistent cycles
  - USDJPY, USDCHF show sharper recent regime transitions

---

## Usage Notes

- Designed for diagnostic tagging, not prediction
- Power can be thresholded for signal confidence
- Easily extended to equities, commodities, or intraday data

---

## Requirements

- Python 3.8+
- NumPy, Pandas, Matplotlib

---

## License

MIT