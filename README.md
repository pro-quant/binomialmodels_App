# Option Pricing Models with Binomial Trees

---

## Navigation
- [Home](#option-pricing-models-with-binomial-trees)  
- [Features](#features)  
- [How to Use](#how-to-use)  
- [Theoretical Background](#theoretical-background)  
  1. [Black–Scholes Formula](#1-blackscholes-formula)  
  2. [Cox–Ross–Rubinstein (CRR) Model](#2-coxrossrubinstein-crr-model)  
  3. [Tian Model](#3-tian-model)  
  4. [Leisen–Reimer Model](#4-leisenreimer-model)  
  5. [Pegged CRR Model](#5-pegged-crr-model)  
- [Reference](#reference)  

---

## Option Pricing Models with Binomial Trees

This app provides an interactive environment to analyze and compare various **Binomial Tree models** for pricing European and American options. It also supports the **Black–Scholes** formula as a benchmark for European options. The app includes **error convergence analysis** for evaluating model performance.

👉 [Launch App](https://binomial-models-app.streamlit.app/)

---

## Preview

<img width="1912" height="954" alt="App Preview" src="https://github.com/user-attachments/assets/ac580cd4-a027-41b4-88e5-2a4e2992afcc" />

---

## Features

### Interactive Option Pricing
- Compute option prices for European and American options.
- Supported models:
  - Cox–Ross–Rubinstein (CRR)  
  - Tian Model  
  - Leisen–Reimer Model  
  - Pegged CRR Model  

### Convergence Analysis
- Visualize the convergence of option prices as the number of time steps increases.  
- Determine the rate of convergence using regression analysis on errors.  

### Black–Scholes Benchmark
- Compute the exact price for European options using the **Black–Scholes** formula.  

### Report Generation
- Export parameters, prices, and convergence plots to an **Excel report**.  

---

## How to Use

1. **Input Parameters**  
   - Enter option parameters: Spot Price (S), Strike Price (K), Time to Maturity (T), Risk-Free Rate (r), and Volatility (σ).  
   - Choose the option type (Call/Put) and style (European/American).  

2. **Select Model**  
   - Choose from CRR, Tian, Leisen–Reimer, or Pegged CRR.  

3. **Convergence Analysis**  
   - Run convergence analysis for European options to study error behavior.  

4. **Export Results**  
   - Generate and download an Excel report containing all results and plots.  

---

## Theoretical Background

### 1. Black–Scholes Formula

The **Black–Scholes model** provides a closed-form solution for European options.  

For a European call or put option, the price is given by:  

![equation](https://latex.codecogs.com/svg.latex?\color{white}C=S_0\Phi(d_1)-Ke^{-rT}\Phi(d_2)\quad\text{(Call)})  

![equation](https://latex.codecogs.com/svg.latex?\color{white}P=Ke^{-rT}\Phi(-d_2)-S_0\Phi(-d_1)\quad\text{(Put)})  

Where:  

![equation](https://latex.codecogs.com/svg.latex?\color{white}d_1=\frac{\ln(S/K)+(r+0.5\sigma^2)T}{\sigma\sqrt{T}},\quad%20d_2=d_1-\sigma\sqrt{T})  

Φ is the cumulative normal distribution.

---

### 2. Cox–Ross–Rubinstein (CRR) Model

A discrete-time binomial tree model where at each step the stock can move up or down:

- Up factor:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}u=e^{\sigma\sqrt{\Delta%20t}})  
- Down factor:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}d=e^{-\sigma\sqrt{\Delta%20t}})  
- Risk-neutral probability:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}q=\frac{e^{r\Delta%20t}-d}{u-d})  

---

### 3. Tian Model

Incorporates second-order moments for improved accuracy:  

- Intermediate variables:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}M=e^{r\Delta%20t},\quad%20V=e^{\sigma^2\Delta%20t})  

- Up and down factors:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}u=\frac{M-V+2\sqrt{V+1+V^2-3}}{2},\quad%20d=\frac{M-V-2\sqrt{V+1+V^2-3}}{2})  

- Risk-neutral probability:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}q=\frac{M-d}{u-d})  

---

### 4. Leisen–Reimer Model

Uses the **Peizer–Pratt inversion method** for binomial distributions to improve convergence.  

- Black–Scholes variables:  
  Growth factor: ![equation](https://latex.codecogs.com/svg.latex?\color{white}a=e^{r\Delta%20t}),  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}d_1), and  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}d_2).  

- Probability approximation:
  

![equation](https://latex.codecogs.com/svg.latex?\color{white}B(z,n)=\tfrac{1}{2}\mp\sqrt{\tfrac{1}{4}-\tfrac{1}{4}e^{-(\tfrac{z}{n+1/3})^2(n+1/6)}})  

- Set:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}p=B(d_2,N),\quad\bar{p}=B(d_2+\sigma\sqrt{T},N))  

- Up and down factors:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}u=a\cdot\frac{\bar{p}}{p},\quad%20d=a\cdot\frac{1-\bar{p}}{1-p})  

---

### 5. Pegged CRR Model

Modified CRR formulation to improve convergence speed:

- Up factor:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}u=e^{\sigma\sqrt{\Delta%20t}+\Delta%20t\ln(K/S)})  
- Down factor:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}d=1/u)  
- Risk-neutral probability:  
  ![equation](https://latex.codecogs.com/svg.latex?\color{white}q=\frac{e^{r\Delta%20t}-d}{u-d})  

---

## Reference

For further theoretical details on binomial models and their implementation, see:  

**Röman, Jan R. M. (2017).**  
*Analytical Finance: Volume I – The Mathematics of Equity Derivatives, Markets, Risk and Valuation.*  
Springer International Publishing. ISBN: 9783319340272.  

Refer to **Chapter 2.7** for binomial tree methods.
