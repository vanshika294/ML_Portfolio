### What is Multicollinearity?

   - Multicollinearity occurs when **two or more independent features (predictors) are highly correlated**.  
  - Example: “Education” and “Training Hours” in a salary dataset are strongly correlated.  

- **Problem it causes:**  
  1. Model finds it hard to **assign individual contributions** to correlated features.  
  2. Coefficients become **unstable** or unintuitive.  
  3. Small changes in the data can lead to **large swings in coefficient values**.  
  4. Standard errors of coefficients are inflated → statistical significance becomes unreliable.


---

### Does it only happen in multivariate regression?

- **Multicollinearity is only relevant when you have multiple predictors**.  
  -  Occurs in **multiple (multivariate) linear regression** or **any regression with more than one feature**.  
  -  Does not occur in **simple linear regression** (one predictor) because there is nothing else to be correlated with.  

---

### How to Detect Multicollinearity

1. **Correlation matrix** – features with high correlation (>0.8 or 0.9) may cause multicollinearity.  
2. **Variance Inflation Factor (VIF)** – a numeric measure of how much the variance of a coefficient is inflated due to correlation with other features.  

---

### How to Handle Multicollinearity

- Remove one of the correlated features.  
- Combine correlated features (e.g., average or principal component).  
- Use regularization techniques like **Ridge** or **Lasso regression**.  

---

### Key Takeaway

> Multicollinearity affects **interpretation of feature weights**, not necessarily the **prediction accuracy**.  
> Always check feature correlations when working with multiple predictors.