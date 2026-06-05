## SHRINKAGE METHODS

# Shrinkage Methods — Intuition Notes

## 1. Why Do We Need Shrinkage?

### Problem with OLS

In linear regression:

ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₚxₚ

OLS learns coefficients by minimizing **training error**:

Loss = Σ(yᵢ − ŷᵢ)²

OLS only asks:

> "What coefficients fit the training data best?"

It does **not** ask:

> "Will these relationships generalize to new data?"

---

### Why is that a problem?

Real datasets contain:

```text
Signal + Noise
```

**Signal:**
- Real patterns

**Noise:**
- Random fluctuations
- Measurement errors
- Accidental correlations

OLS may learn both.

Result:

```text
Very low training error
Higher test error
```

This is called **overfitting**.

---

# 2. Core Idea of Shrinkage

Shrinkage starts with a belief:

> Relationships learned from a finite, noisy dataset should not be trusted completely.

Instead of blindly believing every pattern, shrinkage introduces skepticism.

### OLS mindset

```text
Believe the data completely.
```

### Shrinkage mindset

```text
Trust the data, but cautiously.
```

---

# 3. What Does Shrinkage Actually Do?

Shrinkage modifies the fitting process.

Instead of minimizing only training error:

```text
Loss = Training Error
```

it minimizes:

```text
Loss = Training Error + Penalty
```

---

# 4. What is the Penalty?

**Penalty = Cost for complexity**

The model is punished for having large coefficients.

Think:

```text
Large coefficient
=
Strong claim about a feature
=
Complexity cost
```

### Intuition

OLS:

```text
Fit data as closely as possible.
```

Shrinkage:

```text
Fit data well,
but stay simple.
```

---

# 5. What Does the Penalty Do?

The penalty creates a trade-off:

```text
Prediction accuracy
vs
Model simplicity
```

The model must decide:

> "Is this coefficient large enough to justify its cost?"

---

# 6. Where Does "Evidence" Come From?

Evidence comes only from the training data.

A feature has strong evidence if:

> Including it reduces training error significantly.

A feature has weak evidence if:

> It barely improves the fit.

### Important

The model cannot directly know:

```text
Signal
or
Noise
```

It only sees patterns in data.

---

# 7. Why Shrinkage Helps

Noise variables usually provide:

```text
Small, unstable improvements
```

Real variables usually provide:

```text
Large, consistent improvements
```

When complexity is penalized:

- Weak effects disappear
- Strong effects survive

---

# 8. Ridge Regression (L2)

## Idea

Shrink all coefficients toward zero.

### Objective Function

Loss = Σ(yᵢ − ŷᵢ)² + λΣβⱼ²

where:

- Σ(yᵢ − ŷᵢ)² = training error
- λ = tuning parameter
- Σβⱼ² = Ridge penalty

### Intuition

Every coefficient is attached to zero by a rubber band.

```text
Data pulls coefficient away from zero.
Penalty pulls it back.
```

Final coefficient is a compromise.

### Example

Before:

```text
10   8   5   2
```

After Ridge:

```text
8   6   4   1
```

All coefficients become smaller.

None become exactly zero.

### Key Idea

> Keep all variables, but reduce their influence.

---

# 9. Lasso Regression (L1)

### Objective Function

Loss = Σ(yᵢ − ŷᵢ)² + λΣ|βⱼ|

where:

- Σ(yᵢ − ŷᵢ)² = training error
- λ = tuning parameter
- Σ|βⱼ| = Lasso penalty

### Intuition

Lasso is more aggressive than Ridge.

Instead of merely shrinking coefficients:

> It can eliminate variables completely.

### Example

Before:

```text
10   8   5   2
```

After Lasso:

```text
8   6   3   0
```

Some coefficients become exactly zero.

### Key Idea

> Keep only variables that contribute enough to justify staying in the model.

---

# 10. Elastic Net

### Objective Function

Loss = Σ(yᵢ − ŷᵢ)² + λ₁Σ|βⱼ| + λ₂Σβⱼ²

where:

- λ₁ controls Lasso penalty
- λ₂ controls Ridge penalty

### Intuition

Combines:

```text
Ridge's stability
+
Lasso's feature selection
```

### Key Idea

> Shrink coefficients while allowing some variables to be removed.

---

# 11. Training Error vs Test Error

## Training Error

Error on data used for learning.

```text
Training Error = Σ(y_train − ŷ_train)²
```

## Test Error

Error on new unseen data.

```text
Test Error = Σ(y_test − ŷ_test)²
```

### Goal

We ultimately care about:

```text
Low test error
```

not merely:

```text
Low training error
```

---

# 12. Connection to Bias-Variance Tradeoff

### OLS

```text
Low Bias
High Variance
```

Trusts data completely.

Can overfit.

### Shrinkage

```text
Slightly Higher Bias
Much Lower Variance
```

Trusts data less.

Often predicts better on new data.

---

# 13. One-Line Summary of Each Method

### Ridge

> Shrink all coefficients toward zero but keep every variable.

### Lasso

> Shrink coefficients and remove weak variables completely.

### Elastic Net

> Combine Ridge's stability and Lasso's feature selection.

---

### Summary

> **Shrinkage methods add a penalty during training that discourages large coefficients, forcing the model to learn simpler and more stable relationships that are less likely to be driven by noise and therefore generalize better to unseen data.**