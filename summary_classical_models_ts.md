# Time Series Models: AR, MA, ARMA, ARIMA, SARIMA

This document explains **Autoregression (AR)**, **Moving Average (MA)**, **ARMA**, **ARIMA**, and **SARIMA** models using both formal definitions and intuitive real-world analogies.  

---

## 1. Autoregression (AR)
**Definition:**  
The current value depends on **its own past values**.

**Equation (AR(1)):**  
\[ X_t = \phi_1 X_{t-1} + \epsilon_t \]

**Analogy – Sales Forecasting:**  
- If yesterday’s sales were high, today’s sales are also likely to be high.  
- You’re saying: *“Today’s sales depend on yesterday’s sales.”*  

**Weather analogy:**  
If yesterday was hot, today will also likely be hot.  

---

## 2. Moving Average (MA)
**Definition:**  
The current value depends on **past forecast errors (shocks)**, not past values of the series.

**Equation (MA(1)):**  
\[ X_t = \mu + \theta_1 \epsilon_{t-1} + \epsilon_t \]

**Analogy – Sales Forecasting:**  
- Yesterday you predicted **500 units**, but actual sales were **600 units** (error = +100).  
- The MA model “remembers” that error and says: *“Since I underpredicted yesterday, let me adjust today’s forecast upward.”*  

**Weather analogy:**  
If you forecasted 30°C yesterday but it was actually 35°C, today you’ll adjust upward.  

---

## 3. ARMA (Autoregressive + Moving Average)
**Definition:**  
The current value depends on **both past values** (AR part) **and past errors** (MA part).

**Equation (ARMA(1,1)):**  
\[ X_t = \phi_1 X_{t-1} + \theta_1 \epsilon_{t-1} + \epsilon_t \]

**Analogy – Sales Forecasting:**  
- Today’s sales depend partly on **yesterday’s sales** (AR).  
- But also on whether **your forecast was wrong yesterday** (MA).  

**Weather analogy:**  
- If yesterday was hot, today will probably be hot (AR).  
- But if your forecast was off yesterday, you’ll tweak today’s forecast accordingly (MA).  

---

## 4. ARIMA (Autoregressive Integrated Moving Average)
**Definition:**  
ARIMA extends ARMA by adding **differencing** to handle **trends**.  
- “I” = Integrated = differencing applied to make the series stationary.

**Equation (ARIMA(p,d,q)):**  
- p = AR order  
- d = number of differencing steps  
- q = MA order  

**Analogy – Sales Forecasting:**  
- Suppose sales are growing 10 units per day (trend).  
- ARMA alone struggles with this trend.  
- ARIMA first removes the trend (differencing), models it with ARMA, then reintegrates the forecast.  

**Weather analogy:**  
If the temperature is rising 1°C every day in summer, ARIMA accounts for that trend by differencing.  

---

## 5. SARIMA (Seasonal ARIMA)
**Definition:**  
SARIMA extends ARIMA to handle **seasonality** (patterns repeating at fixed intervals).  
- Adds seasonal AR, seasonal differencing, and seasonal MA components.  

**Equation (SARIMA(p,d,q)(P,D,Q)m):**  
- (p,d,q) = non-seasonal orders  
- (P,D,Q) = seasonal orders  
- m = season length (e.g., 12 for monthly seasonality in yearly data)  

**Analogy – Sales Forecasting:**  
- Ice cream sales peak every summer.  
- Even after accounting for trend (ARIMA), you need a seasonal component to capture these regular summer spikes.  

**Weather analogy:**  
- Winters are always cold, summers are always hot.  
- SARIMA captures this repeating seasonal effect.  

---

# Model Evolution Flow

```
AR   →   MA   →   ARMA   →   ARIMA   →   SARIMA
(past values)  (past errors)  (both)  (+ trend)   (+ seasonality)
```

---

# Final Summary

- **AR → Past values matter.**  
- **MA → Past mistakes matter.**  
- **ARMA → Both matter.**  
- **ARIMA → Both + handles trends (via differencing).**  
- **SARIMA → Both + handles trends + handles seasonality.**  

---

# Use Case Quick Guide:  
- Use **AR** when past values alone explain the series well.  
- Use **MA** when shocks/errors drive the series.  
- Use **ARMA** when both past values and shocks matter.  
- Use **ARIMA** when there’s a **trend**.  
- Use **SARIMA** when there’s both a **trend and seasonality**.  