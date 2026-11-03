# Drivers of U.S. Youth Employment: GDP Growth, Trade, and Minimum Wage

Econometrics term paper, ECON 103A, San José State University (Prof. Sanchita Mukherjee), May 2025. The full paper is the PDF in this repository.

## Question

How have GDP growth, international trade, and the real minimum wage affected employment of U.S. 15–24-year-olds from 1991 to 2024?

## Data

34 annual observations (1991–2024):

| Variable | Description | Source |
|---|---|---|
| youthemp | Youth (15–24) employment rate, % | World Bank |
| GDPgrowth | Real GDP growth, % | FRED |
| ln(import), ln(export) | Log of imports and exports | FRED |
| realminwage | State nominal minimum wages, averaged and CPI-adjusted | FRED |

## Method

Multivariate OLS regression in R:

```
youthemp = β0 + β1·GDPgrowth + β2·ln(import) + β3·ln(export) + β4·realminwage + ε
```

Imports and exports were highly correlated, so a second model combines them into a single log trade-volume variable to address multicollinearity. An F-test checks whether GDP growth, imports, and exports are jointly significant.

## Key results

| | Model 1 (separate trade) | Model 2 (combined trade) |
|---|---:|---:|
| GDP growth | 0.782** | 0.769** |
| ln(imports) | 2.091 | |
| ln(exports) | −8.004 | |
| ln(trade volume) | | −4.509** |
| Real minimum wage | −0.244 | −0.884 |
| R² | 0.735 | 0.724 |

\*\* p < 0.01. N = 34.

- A 1-point rise in GDP growth is associated with about a 0.78-point rise in the youth employment rate.
- Once imports and exports are combined, higher trade volume is associated with significantly lower youth employment.
- The real minimum wage has no statistically significant effect at the national level.
- GDP growth, imports, and exports are jointly significant (F = 6.82 vs. a 5% critical value of about 2.95).

## Limitations

National-level data can hide differences across states; combining imports and exports blurs their separate effects; and factors such as education and industry mix are not modeled.
