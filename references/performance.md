# Performance

## Rule
Do not claim a performance improvement without a measurement before and after. If no measurement tool is available, say "not measured".

## Budgets (starting points, adjust per project)
- Initial JavaScript for a content page: under ~170 KB compressed.
- Largest Contentful Paint target: under 2.5 s on a mid-range phone over a typical connection.
- Interaction latency (INP): under 200 ms.
- Cumulative Layout Shift: under 0.1.

## Images and media
- Serve images at the rendered size; use `srcset` and `sizes`.
- Use modern formats (WebP or AVIF) where the pipeline supports them.
- Set `width` and `height` or an aspect ratio to prevent layout shift.
- Lazy-load below-the-fold images (`loading="lazy"`); do not lazy-load the hero image.
- Compress without visible quality loss.

## JavaScript
- Split code by route and by heavy optional feature (charts, editors, maps).
- Avoid importing whole libraries for one function.
- Remove unused dependencies; check the bundle report for surprises.
- Avoid expensive work in render loops; memoize only where a measurement shows benefit.

## CSS and fonts
- Keep critical CSS small; avoid unused framework layers.
- Limit web fonts to needed weights and subsets; use `font-display: swap` or equivalent.
- Avoid layout thrash: read then write DOM, or use CSS transforms for animation.

## Network and caching
- Cache static assets with content hashes and long lifetimes.
- Use HTTP caching headers for API responses where data freshness allows.
- Batch requests; avoid waterfalls by fetching in parallel when independent.
- Paginate and limit payloads.

## Rendering
- Avoid animating layout properties (top, width, height); animate `transform` and `opacity`.
- Use `content-visibility` or virtualization for very long lists when measured to help.

## Measurement workflow
1. Record the baseline (bundle size, Lighthouse or equivalent, key timings).
2. Make one change.
3. Re-measure and compare.
4. Keep the change only if the gain is real and the code stays clean.
