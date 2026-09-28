---
name: format-homework-plots
description: Improve plot formatting for STAT 432 homework only when the user explicitly asks to use this skill. Do not apply it to unrelated plots or change the statistical analysis.
---

# Format Homework Plots

When explicitly requested, improve the presentation of STAT 432 homework plots without changing the data, calculations, or statistical interpretation.

## Formatting rules

- **Margins and layout:** Leave enough room for titles, tick labels, axis labels, and legends without wasting plotting area. In R, adjust `par(mar=...)` or use a layout helper; in Python, use constrained layout or adjust subplot spacing.
- **Titles:** Give each plot a concise, informative title. For multiple panels, use clear panel titles and avoid repeating information already stated nearby.
- **Axes:** Use sensible limits and readable, uncluttered tick marks. Keep scales honest and consistent when comparing panels.
- **Labels:** Label both axes with the variable or quantity and its units when applicable. Use clear, human-readable wording rather than code variable names.
- **Colors:** Choose a small, high-contrast, color-vision-accessible palette. Do not rely on color alone to distinguish series; combine color with different markers or line styles where useful.
- **Sizes:** Make titles, axis text, labels, lines, and markers legible at the intended output size. Use a consistent hierarchy so titles and labels stand out from ticks and annotations.
- **Portability:** Apply the same principles in R and Python using the plotting system already present. Do not require a particular homework question, dataset, package, or plotting library.
