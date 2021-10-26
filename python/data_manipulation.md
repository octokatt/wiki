---
description: Changing Data Shapes
---


The following snippet sample assigns a value to the column `loc` in the database `new_df`, based on whether it's part of the subset of values where `new_df.population_proper` is above or below 100,000.

```python
new_df.loc[new_df.population_proper < 100000, "location"] = "rural"
new_df.loc[new_df.population_proper >= 100000, "location"] = "urban"

```