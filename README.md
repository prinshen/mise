# Mise

Independent meal planner, separated from `prinshen/mealplanner`.

- App: https://prinshen.github.io/mise/
- Publish the `main` branch root with GitHub Pages. No build step or deployment secrets are required.
- React 18.3.1 and Babel 8.0.4 are pinned. The custom Babel preset explicitly uses the classic React runtime to match the UMD scripts.
- Personal meal plans and the user-entered Anthropic API key remain in browser localStorage under `mise.v1`. This is the same origin and storage key as the original app.
- Protein Log remains at https://prinshen.github.io/mealplanner/protein-log/ with its existing `proteinLog.v1` data. Do not rename or delete that repository or path.
- Service workers must only clean up their own cache prefix. CacheStorage is shared across GitHub Pages projects on this origin.

For future improvements, precompile and bundle JavaScript rather than relying on browser-side Babel. Keep dependency versions pinned and test startup before release.

## Recipe library and text input

- Recipes added to a day are saved automatically in **Opskrifter**. The library supports title/ingredient search, full recipe viewing and reuse on any weekday. Replacing a planned meal asks for confirmation.
- Starting a new week clears the plan and shopping checkmarks, while preserving recipes and pantry items. Recipes in the current plan are migrated into the library on first load. Previously removed recipes cannot be recovered from the old version.
- All data, including the recipe library, stays in the existing browser-local `mise.v1` record. Storage errors show a retry action; unreadable saved data is preserved rather than replaced with an empty plan.
- **Indsæt opskrift som tekst** accepts a complete recipe alongside the existing link, screenshot and manual input options. Text extraction uses the existing Anthropic API key and keeps the input available after an error.
- Explicit Danish/English aliases match common ingredients in pantry comparisons, shopping-list grouping and library searches. Distinct foods such as onion/red onion and milk/coconut milk remain distinct. The dictionary is intentionally bounded; add further aliases in `INGREDIENT_NAMES`.
