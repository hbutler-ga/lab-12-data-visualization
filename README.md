# Module 12 Lab: Data Visualization with Matplotlib and Seaborn

## Lab Overview

In this lab, you will practice creating data visualizations with **Matplotlib** and **Seaborn**.

The goal is not just to make charts. The goal is to choose the right chart for the question you are trying to answer.

You will use the **Palmer Penguins** dataset, which contains measurements for penguins observed across different islands and species.

By the end of this lab, you should be able to:

- Load and inspect a dataset
- Identify numeric and categorical variables
- Create histograms for numeric variables
- Create count plots for categorical variables
- Create scatterplots for numeric relationships
- Create boxplots for numeric vs. categorical comparisons
- Use `hue` to add a grouping variable
- Create subplots
- Create a correlation heatmap
- Export a polished visualization as a `.png` file

---

## Dataset

We will use the `penguins` dataset from Seaborn.

Each row represents one penguin.

Some important columns include:

| Column | Description | Variable Type |
|---|---|---|
| `species` | Penguin species | Categorical |
| `island` | Island where the penguin was observed | Categorical |
| `bill_length_mm` | Bill length in millimeters | Numeric |
| `bill_depth_mm` | Bill depth in millimeters | Numeric |
| `flipper_length_mm` | Flipper length in millimeters | Numeric |
| `body_mass_g` | Body mass in grams | Numeric |
| `sex` | Penguin sex | Categorical |

---

## Setup

Create a new notebook or Python script for this lab.

Start by importing the required libraries and loading the dataset.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

penguins = sns.load_dataset("penguins")

penguins.head()
```

---

## Part 1: Inspect the Dataset

Before creating visualizations, inspect the dataset.

Run the following code:

```python
penguins.shape
```

```python
penguins.info()
```

```python
penguins.describe()
```

```python
penguins.isna().sum()
```

### Question 1

Answer the following questions in a markdown cell or written response:

1. How many rows and columns are in the dataset?
2. Which columns are numeric?
3. Which columns are categorical?
4. Are there any missing values?

---

## Part 2: Handle Missing Values

This dataset has a small number of missing values.

For this lab, create a cleaned version of the dataset by dropping rows with missing values.


### Question 2

Why is it useful to check for missing values before creating visualizations?

---

## Part 3: One Numeric Variable

### Task

Create a histogram showing the distribution of penguin body mass.

Use the column:

```text
body_mass_g
```

### Requirements

Your plot should include:

- `plt.figure(figsize=(10, 6))`
- `sns.histplot()`
- `bins=20`
- a clear title
- a clear x-axis label
- a clear y-axis label
- `plt.show()`

### Question 3

What does the histogram tell you about the distribution of penguin body mass?


---

## Part 4: One Categorical Variable

### Task

Create a count plot showing how many penguins belong to each species.

Use the column:

```text
species
```

### Requirements

Your plot should include:

- `plt.figure(figsize=(8, 5))`
- `sns.countplot()`
- a clear title
- a clear x-axis label
- a clear y-axis label
- `plt.show()`

### Question 4

Which species appears most often in the cleaned dataset?

---

## Part 5: Numeric vs. Numeric

### Task

Create a scatterplot showing the relationship between flipper length and body mass.


### Requirements

Your plot should include:

- `plt.figure(figsize=(10, 6))`
- `sns.scatterplot()`
- `x="flipper_length_mm"`
- `y="body_mass_g"`
- `alpha=0.7`
- a clear title
- clear x- and y-axis labels
- `plt.show()`

### Question 5

What relationship do you notice between flipper length and body mass?

---

## Part 6: Numeric vs. Categorical

### Task

Create a boxplot comparing body mass across species.

Use these columns:

```text
species
body_mass_g
```


### Question 6

How does body mass appear to differ by species?

---

## Part 7: Multiple Variables with `hue`

### Task

Create a scatterplot showing the relationship between flipper length and body mass, colored by species.

Use these columns:

```text
flipper_length_mm
body_mass_g
species
```

### Starter Code

```python
plt.figure(figsize=(10, 6))

sns.scatterplot(data=____, x="____", y="____", hue="____", alpha=____)

plt.title("____")
plt.xlabel("____")
plt.ylabel("____")

plt.show()
```

### Requirements

Your plot should include:

- `plt.figure(figsize=(10, 6))`
- `sns.scatterplot()`
- `x="flipper_length_mm"`
- `y="body_mass_g"`
- `hue="species"`
- `alpha=0.7`
- a clear title
- clear x- and y-axis labels
- `plt.show()`

### Question 7

What does adding `hue="species"` help you see?

---

## Part 8: Subplots

### Task

Create three histograms side by side showing the distributions of:

- `bill_length_mm`
- `bill_depth_mm`
- `body_mass_g`


### Requirements

Your subplot figure should include:

- one row
- three columns
- three histograms
- clear titles
- clear x-axis labels
- `plt.tight_layout()`
- `plt.show()`

### Question 8

Why might subplots be useful when comparing several related variables?

---

## Part 9: Correlation Heatmap

### Task

Create a correlation heatmap for the numeric columns in the cleaned penguins dataset.

### Requirements

Your heatmap should include:

- selected numeric columns
- `.corr()`
- `sns.heatmap()`
- `annot=True`
- `cmap="coolwarm"`
- `center=0`
- a clear title
- `plt.show()`

### Question 9

Which two variables appear to have the strongest positive relationship?

---

## Part 10: Line Plot Reflection

The lesson used a line plot with the `mpg` dataset because it had an ordered variable: `model_year`.

The penguins dataset does not have a clear time or ordered sequence variable.

### Question 10

Why might a line plot not be the best default chart for this dataset?

In your answer, mention the importance of having an ordered x-axis.

---

## Part 11: Export a Polished Visualization

### Task

Choose one visualization from this lab and polish it for export.

Your final visualization should include:

- an appropriate chart type
- a clear title
- clear x- and y-axis labels
- an appropriate figure size
- `plt.tight_layout()`
- export as a `.png` file using `plt.savefig()`


### Important Note

Call `plt.savefig()` before `plt.show()`.

Preferred:

```python
plt.savefig("my_plot.png", dpi=300, bbox_inches="tight")
plt.show()
```

Avoid:

```python
plt.show()
plt.savefig("my_plot.png", dpi=300, bbox_inches="tight")
```

In some environments, calling `plt.show()` first can clear or finalize the figure before it is saved.

---

## Final Deliverables

Submit the following:

1. A completed notebook or Python script
2. All required visualizations
3. Written answers to the reflection questions
4. One exported `.png` visualization

---

## Reflection Questions Summary

Answer these questions before submitting:

1. How many rows and columns are in the dataset?
2. Which columns are numeric? Which are categorical?
3. Why is it useful to check for missing values before visualizing?
4. What does the body mass histogram tell you?
5. Which species appears most often?
6. What relationship do you notice between flipper length and body mass?
7. How does body mass appear to differ by species?
8. What does adding `hue="species"` help you see?
9. Why are subplots useful when comparing related variables?
10. Which two variables appear to have the strongest positive relationship in the heatmap?
11. Why might a line plot not be the best default chart for this dataset?
12. Which visualization did you choose to export, and why?

---

## Suggested Rubric

| Criteria | Points |
|---|---:|
| Loads and inspects dataset correctly | 10 |
| Handles missing values appropriately | 10 |
| Creates required histogram | 10 |
| Creates required count plot | 10 |
| Creates required scatterplot | 10 |
| Creates required boxplot | 10 |
| Uses `hue` appropriately | 10 |
| Creates subplots correctly | 10 |
| Creates heatmap correctly | 10 |
| Exports polished visualization as `.png` | 10 |
| **Total** | **100** |

---

## Key Takeaway

A good visualization starts with a question.

Before choosing a chart, ask:

1. What question am I trying to answer?
2. Which columns do I need?
3. Are those columns numeric, categorical, or ordered?
4. Which chart type fits the question and variable types?

The chart should make the pattern easier to understand.
