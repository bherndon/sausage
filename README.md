# Herndon Sausage Calculator

A simple, phone-friendly calculator for the Herndon family's sausage, jerky and BBQ recipes. Pick a recipe, enter how much you're making, and every ingredient scales automatically.

**Live site:** https://bherndon.github.io/sausage/

## Features

- **41 recipes in 8 categories**, picked from pill-style dropdowns: Family, Pork & Venison, Flavored, Burgers, Jerky, Brine, BBQ and Sides.
- **Instant scaling:** enter pounds of meat, total batch weight, pounds of seasoning, or number of batches, depending on the recipe.
- **Easy-to-read units:** spices show in tsp, tbsp or cups (whichever is easiest to measure), and weighed ingredients show in oz, lb and grams.
- **Check-off list:** tap an ingredient as you add it. Checked items move to the bottom, so what's left is always at the top.
- **Remembers your place:** your last recipe, amount and checks are saved in your browser.
- **Processing notes:** cure, smoking, grinding and cooking-temperature tips appear on the recipes they apply to.
- **Feedback form:** the "Submit feedback" button in the header sends a message, with the sender's email for replies.
- **Light and dark mode:** follows your device setting.

## Recipes

| Category | Recipes | Scaled by |
| --- | --- | --- |
| Family | Herndon Sausage, Jerrell Texas Sausage, Hot Link, Deer Bologna, Original Herndon (50 lb) | Pounds of meat |
| Pork & Venison | Regular, Jalapeño & Cheese, Spicy, Andouille, Fresh Bratwurst, Fresh Pan Sausage, Hot Dogs, Italian, Fresh Chorizo, English Banger, Salami Lunchmeat, Pepperoni | Total batch weight |
| Flavored | Spinach & Feta, Apple / Cranberry, Bacon Cheddar, Sun-Dried Tomato & Feta | Total batch weight |
| Burgers | Bacon Venison, Bacon Cheddar Venison, Jalapeño Cheddar, Mushroom Swiss, Blue Cheese, Roasted Garlic & Feta | Total batch weight |
| Jerky | Jerky Seasoning | Pounds of seasoning |
| Brine | Apple Spice Turkey Brine | Batches |
| BBQ | Mustard Sauce, Red Sauce, Pork Injection, Pork Rub, Brisket Rub, Chicken Brine, Chicken Wings, Chicken Thighs | Batches |
| Sides | Mac and Cheese, Pinto Beans, Bean Seasoning, Cole Slaw | Batches |

## Food safety

- Add cure (sodium nitrite / Tender Quick) **only** to sausage you're going to smoke, and measure it carefully. Never round it up.
- Cook sausage to 165–170°F internal, then chill to 40°F quickly.
- These are family recipes, not tested commercial formulas. Use your own judgment.

## How it's built

Everything lives in one file, `index.html`: plain HTML, CSS and JavaScript with no build step and no dependencies (fonts load from Google Fonts). GitHub Pages serves it straight from the `main` branch.

Feedback goes through [FormSubmit](https://formsubmit.co), a free form-to-email service. The form uses FormSubmit's private code instead of an email address, so no address appears in the code.

## Editing recipes

Recipes are defined in the `RECIPES` list near the top of the `<script>` in `index.html`. Each recipe looks like this:

```js
{ id:"herndon", group:"Family recipes (per lb of meat)", name:"Herndon Sausage",
  mode:"meat", base:1, start:25,
  desc:"Ground pork, or a 55/45 pork/venison mix.",
  items:[["Salt",0.40,"tbsp"], ["Black pepper",0.72,"tsp","50/50 coarse and fine"]] }
```

- **mode:** `meat` (pounds of meat), `batch` (total batch weight), `season` (pounds of seasoning) or `mult` (number of batches).
- **base:** the amount the ingredient quantities are written for (for example, `1` for per-pound recipes or `100` for a 100 lb formula).
- **start:** the default amount shown when the recipe is first opened.
- **items:** `[name, amount at base, unit, optional note]`. Units: `tsp`, `tbsp`, `cup` (volume), `lb`, `oz` (weight), or any word for a count (`cans`, `cloves`, `whole`). A plain string such as `"Sauce"` starts a sub-section.
- **tips:** optional list of notes shown under the amount box.

Commit a change to `index.html` and the live site updates within a few minutes. Hard-refresh (Cmd/Ctrl + Shift + R) if you still see the old version.
