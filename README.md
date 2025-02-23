# -U.S.-Treasury-Yield-Curve-Modeling-with-Nelson-Siegel
## Overview
This project implements the **Nelson-Siegel yield curve model** to analyze U.S. Treasury yields using real market data from **FRED** (Federal Reserve Economic Data). The yield curve is fitted using **nonlinear optimization techniques** to estimate key parameters, ensuring an accurate representation of market interest rates. Additionally, a **Butterfly Spread** trading strategy is employed to capture changes in yield curve convexity.

## Nelson-Siegel Model
The Nelson-Siegel model is defined as:

$$
Y(t) = \beta_0 + \beta_1 \frac{1 - e^{-t/\tau}}{t/\tau} + \beta_2 \left(\frac{1 - e^{-t/\tau}}{t/\tau} - e^{-t/\tau}\right)
$$

where:
- $\beta_0$ represents the **long-term interest rate level**.
- $\beta_1$ captures the **short-term rate dynamics**.
- $\beta_2$ accounts for the **medium-term hump effect**.
- $\tau$ governs the **speed of exponential decay** in the yield curve.

## Butterfly Spread Trading Strategy
A **Butterfly Spread** is used to capture convexity changes in the yield curve. The spread is computed as:

$$
\text{Butterfly Spread} = 2 \times Y_{5Y} - (Y_{2Y} + Y_{10Y})
$$

### Trading Signals:
- **Rising Butterfly Spread** → **Steepening yield curve**, suggesting a **long butterfly trade** (Buy 5Y, Short 2Y & 10Y).
- **Declining Butterfly Spread** → **Flattening yield curve**, favoring a **short butterfly trade** (Short 5Y, Buy 2Y & 10Y).

## Implementation
- **Data Source**: U.S. Treasury yields from **FRED** (via `pandas_datareader`).
- **Libraries Used**: `NumPy`, `pandas`, `matplotlib`, `scipy.optimize`.
- **Optimization**: The `scipy.optimize.minimize` function is used for parameter estimation.
- **Visualization**: Yield curve fitting and Butterfly Spread trends are plotted using `matplotlib`.

## Installation & Usage
```bash
# Clone the repository
git clone https://github.com/yourusername/nelson-siegel-yield-curve.git
cd nelson-siegel-yield-curve

# Install dependencies
pip install numpy pandas matplotlib scipy pandas_datareader

# Run the script
python yield_curve_model.py
```

## Output
The python code generates:
1. **Yield Curve Fitting** plot compares observed and Nelson-Siegel fitted yields.
2. **Butterfly Spread Trading Signal** plot shows the convexity trends over time.


## License
This project is licensed under the MIT License. Feel free to use and modify it as needed!
