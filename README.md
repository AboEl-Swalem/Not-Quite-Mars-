# Not Quite Mars?

Finds Earth analogs for the Moon by matching terrain slope. NASA Space Apps Challenge 2026.


## The Problem
We can't test on the Moon or Mars before launch, so we look for Earth locations that resemble them.
Gravity can't be simulated, so we match terrain slope.

## What We Built
- Cleaned and prepared lunar and Earth elevation data
- Calculated slope at every point from its 12 nearest neighbors within 2.5 km
- Built an interactive map: click a point on the Moon and get the best-matching Earth location

## Results
| Moon slope | Marmara slope | Difference | Match |
|---|---|---|---|
| 0.016319° | 0.016323° | 0.000004° | 99.98% |

Best match: 40.1167°N, 28.1579°E (Marmara, Turkey)

## How It Works
1. Convert coordinates to meters (EPSG:32635 for Marmara)
2. Find the 12 nearest neighbors within 2.5 km
3. Fit a plane to their elevations (least squares)
4. Slope = arctan(√(a² + b²))
5. Match each Moon point to the Marmara point with the closest slope

## Data Sources
- NASA LRO LOLA GDR, from the NASA PDS Geosciences Node
- MODIS LST & DEM for Marmara, Umut Alkan, Kaggle, 2025 (DOI: 10.34740/KAGGLE/DSV/11200689)

## Getting Started
```bash
git clone <repo-url>
cd <repo>
pip install -r requirements.txt
```
Open `notebook.ipynb` and run all cells. Place the datasets in `data/` first.
Open `Lunar_Marmara_Interactive_Matching.html` in a browser to try the map.

## Limitations and Future Work
- Matching uses slope only; temperature, soil and humidity are not included yet
- Moon analysis used a subset of about 1 million points
- Next: add Mars data and more parameters

## Team
Mariam Hassan · Ahmed El-Banna · Abd Al-Rahman Salem

## License
MIT 
