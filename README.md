# 102303812-TOPSIS

A Python package implementing **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** for multi-criteria decision analysis and ranking of alternatives.

**Author:** Harsh Tanwar
**Roll No:** 102303812
**Institute:** Thapar Institute of Engineering & Technology

[![PyPI](https://img.shields.io/pypi/v/102303812-topsis)](https://pypi.org/project/102303812-topsis/)
[![Python](https://img.shields.io/badge/Python-3.6%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## Overview

**TOPSIS** (Technique for Order Preference by Similarity to Ideal Solution) is a **Multi-Criteria Decision-Making (MCDM)** technique used to rank alternatives based on multiple criteria.

The method determines how close each alternative is to:

* **Ideal Positive Solution** — the best value for every criterion.
* **Ideal Negative Solution** — the worst value for every criterion.

An alternative that is closer to the ideal positive solution and farther from the ideal negative solution receives a higher TOPSIS score and a better rank.

This implementation provides a simple **command-line interface (CLI)** for performing TOPSIS analysis on CSV datasets.

---

## Features

* Implements the complete TOPSIS algorithm
* Supports multiple alternatives and criteria
* Supports weighted criteria
* Supports beneficial (`+`) and non-beneficial (`-`) criteria
* Performs vector normalization
* Calculates ideal positive and ideal negative solutions
* Calculates Euclidean distances
* Generates TOPSIS scores
* Automatically ranks alternatives
* Reads input data from CSV files
* Generates results as a CSV file
* Available as a Python package through PyPI

---

## TOPSIS Algorithm

The implementation follows these steps:

1. Construct the decision matrix
2. Normalize the decision matrix using vector normalization
3. Apply the user-defined weights
4. Determine the ideal positive and ideal negative solutions
5. Calculate Euclidean distances from both ideal solutions
6. Compute the TOPSIS score for each alternative
7. Rank alternatives based on their scores

A higher score indicates an alternative is closer to the ideal positive solution and farther from the ideal negative solution.

---

## Requirements

* Python **3.6+**
* **pandas** — data handling
* **NumPy** — numerical operations

Install the dependencies:

```bash
pip install pandas numpy
```

---

## Installation

### Install from PyPI

The package can be installed directly using pip:

```bash
pip install 102303812-topsis
```

### Install from Source

Clone the repository:

```bash
git clone https://github.com/htan35/Topsis.git
```

Navigate to the project directory:

```bash
cd Topsis
```

Install the package:

```bash
pip install .
```

---

## Usage

The package provides a command-line interface:

```bash
topsis <InputDataFile> <Weights> <Impacts> <OutputResultFileName>
```

### Example

```bash
topsis data.csv "1,1,1,1,1" "+,+,-,+,-" result.csv
```

Where:

```text
InputDataFile        = data.csv
Weights              = 1,1,1,1,1
Impacts              = +,+,-,+,-
OutputResultFileName = result.csv
```

---

## Parameters

| Parameter              | Description                                             |
| ---------------------- | ------------------------------------------------------- |
| `InputDataFile`        | Path to the input CSV file                              |
| `Weights`              | Comma-separated weights for each criterion              |
| `Impacts`              | Comma-separated impacts (`+` or `-`) for each criterion |
| `OutputResultFileName` | Name/path of the output CSV file                        |

### Weights

Weights represent the relative importance of each criterion.

Example:

```text
1,1,1,2,1
```

The number of weights must match the number of criteria.

### Impacts

Impacts specify whether higher or lower values are preferred.

```text
+  → Higher value is preferred
-  → Lower value is preferred
```

Example:

```text
+,+,-,+,-
```

---

## Input File Format

The input file must be a CSV containing:

* A header row
* The first column containing alternative names
* Remaining columns containing numerical criterion values

### Example

| Product | Quality | Price | Features | Customer Rating | Delivery Time |
| ------- | ------: | ----: | -------: | --------------: | ------------: |
| A1      |     8.5 |   450 |      7.2 |             4.3 |             3 |
| A2      |     7.8 |   380 |      8.1 |             4.5 |             5 |
| A3      |     9.1 |   520 |      8.8 |             4.1 |             4 |

In this example:

* `Product` → Alternative name
* `Quality` → Criterion 1
* `Price` → Criterion 2
* `Features` → Criterion 3
* `Customer Rating` → Criterion 4
* `Delivery Time` → Criterion 5

---

## Example

For the dataset above:

### Weights

```text
1,1,1,1,1
```

All criteria have equal importance.

### Impacts

```text
+,+,-,+,-
```

This means:

| Criterion       | Impact | Preference       |
| --------------- | ------ | ---------------- |
| Quality         | `+`    | Higher is better |
| Price           | `+`    | Higher is better |
| Features        | `-`    | Lower is better  |
| Customer Rating | `+`    | Higher is better |
| Delivery Time   | `-`    | Lower is better  |

Run:

```bash
topsis data.csv "1,1,1,1,1" "+,+,-,+,-" result.csv
```

---

## Output

The generated output CSV contains all the original columns along with two additional columns:

### Topsis Score

Represents the relative closeness of an alternative to the ideal solution.

The score lies between:

```text
0 ≤ Topsis Score ≤ 1
```

### Rank

Represents the ranking of each alternative.

```text
1 = Highest-ranked alternative
```

Example output structure:

| Product | Quality | Price | Features | Customer Rating | Delivery Time | Topsis Score | Rank |
| ------- | ------: | ----: | -------: | --------------: | ------------: | -----------: | ---: |
| A1      |     8.5 |   450 |      7.2 |             4.3 |             3 |         0.72 |    2 |
| A2      |     7.8 |   380 |      8.1 |             4.5 |             5 |         0.64 |    3 |
| A3      |     9.1 |   520 |      8.8 |             4.1 |             4 |         0.81 |    1 |

The actual results depend on the input data, weights, and impacts.

---

## Python Usage

The package can also be invoked from Python:

```python
import importlib

topsis = getattr(
    importlib.import_module("102303812-topsis"),
    "topsis"
)

topsis(
    "data.csv",
    "1,1,1,1,1",
    "+,+,-,+,-",
    "result.csv"
)
```

---

## Package Information

| Property       | Details                      |
| -------------- | ---------------------------- |
| Package Name   | `102303812-topsis`           |
| Language       | Python                       |
| Python Version | 3.6+                         |
| Libraries      | Pandas, NumPy                |
| Interface      | Command Line + Python Module |
| Input          | CSV                          |
| Output         | CSV                          |
| License        | MIT                          |

---

## Project Structure

```text
Topsis/
│
├── README.md
├── setup.py
├── data.csv
├── LICENSE
│
└── Topsis_HarshTanwar_102303812/
    ├── __init__.py
    └── topsis.py
```

---

## Links

### GitHub Repository

https://github.com/htan35/Topsis

### PyPI Package

https://pypi.org/project/102303812-topsis/

### Alternate PyPI Listing

https://pypi.org/project/Topsis-HarshTanwar-102303812/

### Google Colab

https://colab.research.google.com/drive/1hFhuzNVxJ53LJTjMrJsID8C_r-0W3Nya?usp=sharing

---

## Author

**Harsh Tanwar**

Computer Engineering
Thapar Institute of Engineering & Technology

GitHub: https://github.com/htan35

Email: [htanwar_be23@thapar.edu](mailto:htanwar_be23@thapar.edu)

---

## License

This project is licensed under the **MIT License**.

See [LICENSE](LICENSE) for more details.
