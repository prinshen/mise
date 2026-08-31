# Mise

Independent meal planner, separated from `prinshen/mealplanner`.

- App: https://prinshen.github.io/mise/
- Publish the `main` branch root with GitHub Pages. No build step or deployment secrets are required.
- React 18.3.1 and Babel 8.0.4 are pinned. The custom Babel preset explicitly uses the classic React runtime to match the UMD scripts.
- Personal meal plans and the user-entered Anthropic API key remain in browser localStorage under `mise.v1`. This is the same origin and storage key as the original app.
- Protein Log remains at https://prinshen.github.io/mealplanner/protein-log/ with its existing `proteinLog.v1` data. Do not rename or delete that repository or path.
- Service workers must only clean up their own cache prefix. CacheStorage is shared across GitHub Pages projects on this origin.

For future improvements, precompile and bundle JavaScript rather than relying on browser-side Babel. Keep dependency versions pinned and test startup before release.
