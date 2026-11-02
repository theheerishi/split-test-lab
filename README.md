Split Test Lab
An A/B test significance calculator for marketers. Enter the visitors and conversions for two variants and it tells you whether the difference is statistically real or just noise, with the confidence level, p-value, and a confidence-interval comparison chart. Single file, pure client-side, no backend.

Run
It's a single static index.html. Open it directly in a browser, or serve it:

npx serve .
Deploy anywhere static (Vercel, Netlify, GitHub Pages) by pointing at the folder. No build step, no dependencies.

What it does
Two-proportion z-test (two-tailed) comparing the conversion rates of a control and a variant
Verdict at a chosen threshold (90% / 95% / 99%): significant win, significant loss, or not yet significant
Metrics: relative change, confidence, p-value, z-score
Chart: each variant's conversion rate with its confidence interval, so you can see how much the intervals overlap
Method
Step	Formula
Conversion rate	conversions ÷ visitors
Pooled rate	(cA + cB) ÷ (nA + nB)
Standard error	√( pooled × (1 − pooled) × (1/nA + 1/nB) )
z-score	(pB − pA) ÷ SE
p-value	2 × (1 − Φ(|z|)), two-tailed
Confidence	(1 − p) × 100
Interval (per variant)	p ± zc × √( p(1 − p) ÷ n )
The normal CDF uses the Abramowitz & Stegun 7.1.26 approximation for the error function.

Stack
Plain HTML, CSS, and vanilla JavaScript in one file
IBM Plex Sans and IBM Plex Mono for the UI and figures
Inline SVG for the comparison chart
Light and dark themes, responsive to phone width
Note
This measures statistical significance, not test duration or power. Keep your sample sizes balanced and avoid stopping a test the moment it crosses the line.
