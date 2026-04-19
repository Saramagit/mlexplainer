# Visual ML Explainer

**Interactive visualizations for learning classical machine learning.** Drag data, tune real scikit-learn hyperparameters, and watch the models respond live. No code or math required.

🔗 **Live demo:** [saramagit.github.io/mlexplainer](https://saramagit.github.io/mlexplainer/)

![Visual ML Explainer demo — dragging the applicant across the decision boundary in a k-NN classifier](mlexplainer_demo.gif)

---

## What's inside

Seven interactive method explainers plus an evaluation toolkit, each with real hyperparameter controls:

| Lesson | What you'll tune | What you'll see |
|---|---|---|
| **Principal Component Analysis** | `n_components`, scaling on/off, `svd_solver` | Scree plot, cumulative variance, 2D projection |
| **Evaluation Metrics** (classifier toolkit) | Decision threshold, FP cost, FN cost | Score distribution, ROC curve, confusion matrix, cost-optimal threshold |
| **Linear Regression** | Method (OLS/Ridge/Lasso), `alpha`, `test_size` | Fit line, residuals, OLS reference, R² gap |
| **k-Nearest Neighbors** | `n_neighbors`, `metric`, `weights`, scaling | Decision boundary, neighbor links, live prediction |
| **Naive Bayes** | `alpha` (Laplace smoothing), `fit_prior`, class prior | Word-by-word spam probability, log-likelihood breakdown |
| **Decision Trees** | `max_depth`, `min_samples_split`, `min_samples_leaf`, `criterion` | Decision regions, tree rules, train-test gap |
| **Logistic Regression** | `C`, `penalty` (L1/L2), `class_weight`, threshold | Probability heatmap, sigmoid boundary, coefficient values |
| **Linear & Quadratic Discriminant Analysis** | Classifier (LDA/QDA), `shrinkage`, priors, spreads | Decision regions, Gaussian boundary, class overlap |

Every control uses the **actual scikit-learn parameter name** alongside a plain-language description of what it does.

## Who this is for

Learners who want to build intuition for how machine learning models actually behave before or alongside reading about the math.

- Students in introductory ML or data mining courses
- Professionals moving into analytics roles who need a mental model
- Anyone who finds textbook explanations dense and would rather poke at something

No Python, no math prerequisites, no setup. Runs entirely in the browser.

## Quick tour — 3 things to try first

If you're new to the tool, these three interactions will teach you something real in under 5 minutes each:

**1. See overfitting happen live in Decision Trees.**  Open the Decision Trees lesson. Crank `max_depth` from 3 up to 10 and set `min_samples_leaf` to 1. Watch the train-test accuracy gap turn red (that's the overfit alert). Now raise `min_samples_leaf` back to 5 and watch the gap close.

**2. Find the single most common production bug in k-NN.**  Open the k-NN lesson. Turn `StandardScaler()` to Off and crank `income_scale` to 10×. The decision boundary collapses to a vertical line — k-NN is now using income almost exclusively. The narrative panel flashes a red alert explaining why. This is a bug that costs real teams real money.

**3. Watch an optimal threshold shift with business costs.**  Open the Evaluation lesson. Set `fn_cost` to $50 and `fp_cost` to $5 (a fraud-detection cost ratio). Note the "Cost-optimal threshold" value — around 0.2. Click "Jump to cost-optimal threshold." Now flip the costs: `fn_cost` $5, `fp_cost` $50 (spam-filter costs). Watch the optimal threshold migrate to 0.8. Same model, different business, completely different decision.

## Design principles

- **Real hyperparameters, not toy sliders.** Controls match what you'd actually type in scikit-learn.
- **Live feedback.** Every slider move updates all metrics immediately. No "click to apply" buttons.
- **Narrative explanations.** A text panel names what's happening ("Overfitting alert", "Good generalization", "L1 feature selection") as you tune.
- **Train/test split visualized.** Rings around test points. Gap between train and test accuracy flagged in red when overfitting begins.
- **Comparison tracking.** Deltas since your last change, shown with arrows and colors, so you can see the effect of each adjustment.

## Running locally

No build step, no dependencies to install.

```bash
git clone https://github.com/Saramagit/mlexplainer.git
cd mlexplainer
open index.html
```

Or just download `index.html` and open it in any modern browser.

## Tech stack

Single self-contained HTML file. Vanilla JavaScript. Inline SVG for visualizations. No frameworks, no build tooling, no backend, no analytics, no tracking.

- **Fonts:** DM Serif Display, Outfit, IBM Plex Mono (via Google Fonts)
- **Total size:** ~170 KB
- **Works on:** Desktop, tablet, mobile (with some compromises on narrow viewports)

## Using this in your own teaching

You're welcome to link to the live site or fork the code for your own course. A few tips:

- **Project in class** by sharing your browser. The interactions read well from the back of a room.
- **Assign a lesson before reading.** Students build intuition from the tool, then the textbook makes more sense.
- **Pair exercises.** "Find a hyperparameter setting where the train-test gap goes above 15 points, then find one that closes it to under 3 points. Explain both in one sentence."

If you build something educational on top of this — a lesson plan, a worksheet, a translation — I'd love to hear about it via [GitHub Issues](https://github.com/Saramagit/mlexplainer/issues).

## Inspirations

This project owes a creative debt to:

- [Seeing Theory](https://seeing-theory.brown.edu) — Brown's interactive probability and statistics visualizer
- [Distill.pub](https://distill.pub) — interactive ML research publications
- [Brendan Bycroft's LLM Visualization](https://bbycroft.net/llm) — for showing what's possible when you commit deeply to one thing
- The [scikit-learn documentation](https://scikit-learn.org) — for making the actual parameter names clear enough to teach

## Author

Built by **Sarama Shehmir**. Originally created as a teaching companion for a graduate analytics course, then cleaned up and released publicly.

## License

MIT. See [LICENSE](LICENSE). You're free to use, modify, redistribute, or fork this for any purpose — commercial, academic, personal. Attribution is appreciated but not required.

## Contributing

Bug reports, feature suggestions, and accessibility improvements are all welcome via [GitHub Issues](https://github.com/Saramagit/mlexplainer/issues).

If you'd like to add a new method or substantially change a visualization, please open an issue first so we can discuss the approach before you invest time in a pull request.
