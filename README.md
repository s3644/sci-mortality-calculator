# SCI-PReSS — Complication Risk Calculator

**Multi-complication screening for spinal cord injury**  
NSCISC 2021 · 35,675 patients · 134,351 visits · Mean AUC 0.702 (V5) · 16 outcomes

**Live:** https://s3644.github.io/sci-mortality-calculator/

---

## What It Does

SCI-PReSS predicts 16 SCI complication risks from 10 clinical questions and generates risk-stratified monitoring schedules with evidence-based clinical actions.

| Feature | Detail |
|---|---|
| **Inputs** | 10 questions (age, sex, AIS grade, neuro level, BMI, complication count, FIM, etiology, education, marital status) |
| **Outputs** | 16 complication risk estimates + 4-tier schedule + survival estimate + clinical actions |
| **Tiers** | Low → Moderate → High → Critical |
| **Model** | V5 RF/XGB/LGBM ensemble, 48 features per target |

## V6 Enhancements

- **Missingness-aware scoring** — Detects default values and applies Code-9 penalty (mirrors finding that unmeasured patients are systematically higher risk)
- **Real V5 thresholds** — From trained models (`v5_fixed_results.json`)
- **Key interactions** — Care gap × AIS, Cervical + AIS A, Age × data gaps
- **Care gap index** — Quantifies data completeness impact on risk

## Architecture

- Pure client-side JavaScript — no server required
- All computation runs in the browser
- Responsive design (mobile + desktop)
- Collapsible field reference guide

## Files

| File | Description |
|---|---|
| `index.html` | SCI-PReSS V6 calculator |
| `cox_model.json` | Cox PH survival model coefficients (C-index 0.82, 85 features) |

## Author

**Jukrapope Jitpimolmard, MD**  
[ORCID: 0009-0001-9170-426X](https://orcid.org/0009-0001-9170-426X)

## Citation

```
Jitpimolmard J. SCI-PReSS Complication Risk Calculator. 2026.
https://github.com/s3644/sci-mortality-calculator
```

## Disclaimer

⚠️ Screening tool only. Not for clinical use without prospective validation. Clinical judgment supersedes ML predictions. This is a research tool developed from retrospective NSCISC 2021 data.
