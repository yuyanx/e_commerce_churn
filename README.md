# e_commerce_churn

## Explain Feature Importance

In this project, **feature importance** answers: *which inputs influence churn predictions the most?*.

### How feature importance is computed here

The notebook evaluates a Random Forest model and then uses:

1. `model.feature_importances_` (tree-based importance)
2. SHAP summary plots (`shap.TreeExplainer`) for direction + magnitude of impact

Tree-based importance scores are normalized so their total is 1. A higher value means a feature is used more often and/or more effectively to reduce impurity across the forest.

### How to interpret it correctly

- **Higher importance ≠ causal effect**. It means predictive usefulness, not business causation.
- **Correlated features can split importance** across each other.
- **Importance is model-specific** (Random Forest importance may differ from Logistic Regression coefficients).
- Use SHAP with global importance to understand both:
  - which features matter most overall
  - whether higher/lower values increase churn risk

### Practical business readout

Use feature importance to prioritize retention actions:

- Monitor the top-ranked drivers weekly.
- Build interventions around high-impact, controllable variables (for example engagement, order behavior, complaints, and loyalty incentives).
- Recompute importance after retraining to detect drift in churn behavior.

### Related notebook sections

See the notebook cells that define:

- `show_feature_importance(model)` (bar chart from `feature_importances_`)
- SHAP explanation with `TreeExplainer` + `summary_plot`
