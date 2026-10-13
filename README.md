# World Military Power 2020 – Country Clustering with K-Means

Unsupervised learning on the **World Military Power 2020** dataset (Global Firepower indicators for 138 countries): grouping countries with similar military capabilities.

## Approach
- **28 indicators** covering air, land and naval forces, defense spending, manpower, natural resources, logistics and geography.
- **Data quality:** a row misalignment that had placed South Korea's naval data (including 22 submarines) in landlocked South Sudan's row was found and corrected; number fields stored as text with Indian-style separators were converted to numbers.
- **Structural missing values:** naval and coastline values are missing for landlocked countries and border length for island nations, so they were filled with 0 rather than imputed.
- **Skewness:** variables were heavily right-skewed (up to 10), so a log transformation was applied before standardisation.
- The composite **Military Strength Power Index** was left out of the model and used afterwards only to validate the clusters.
- **K-Means** with elbow method and silhouette analysis; **k = 3** selected (silhouette 0.245).

## Results
| Cluster | Countries | Median aircraft | Median tanks | Median defense budget | Median Power Index |
|---|---|---|---|---|---|
| Major Powers | 10 | 1,605 | 3,057 | $48.5 bn | 0.15 |
| Regional Powers | 55 | 276 | 420 | $5.05 bn | 0.62 |
| Limited Capacity | 73 | 33 | 44 | $0.35 bn | 2.01 |

**Major Powers:** United States, Russia, China, India, Japan, South Korea, France, United Kingdom, Egypt, Italy.

The Power Index, which was not used in the model, follows the same order (lower index = stronger military), independently confirming the clusters.

## Limitations
- The relatively low silhouette score suggests countries form a continuum rather than sharply separated groups.
- Size-related variables (population, land area, coastline) place small but wealthy countries such as Switzerland, Belgium and Qatar alongside much weaker militaries.
- The data counts equipment but not its quality or technology, which is why Egypt falls among the Major Powers while Germany is a Regional Power.

**Further work:** cluster on military variables only, use per-capita or per-GDP indicators, or test hierarchical clustering.

## Files
- `world-military-power-clustering.ipynb` – full notebook with code, charts and cluster profiles

## Tools
Python · pandas · scikit-learn · matplotlib · seaborn

---
Part of my [data science portfolio](https://betulcelep.github.io/#data-science), completed during the *Mastering Applied Data Science with Deep Learning* programme.
