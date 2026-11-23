# NVDA Max-Profit Analyzer

**CPS 3440 Analysis of Algorithms, Fall 2026, New Jersey City University**

We analyze historical NVIDIA (NVDA) stock prices to find the best day to buy and the best day to sell, using three algorithms of different speeds. We then benchmark how each one scales as the data grows. This project is analysis of past prices, **not price prediction**.

## 1. Problem description
Given a list of daily closing prices, which single buy day and later sell day would have produced the largest profit? This is equivalent to the maximum-subarray problem on the daily price changes. We compare a slow baseline, a divide-and-conquer approach, and a linear-time approach to show how algorithm choice affects speed on real financial data.

## 2. Screenshot / visualization
TODO: add `figures/runtime.png` (runtime vs. input size) and a price chart with the best buy/sell window highlighted.

![Runtime vs input size](figures/runtime.png)

## 3. Dataset and source
- **Source:** [Nvidia Historical Stock Data (Kaggle)](https://www.kaggle.com/datasets/acarmehmet/nvidia-historical-stock-data)
- **Records and date range:** TODO
- **Fields used:** Date, Close
- **Preprocessing:** sorted by date; rows with a missing date or price removed. TODO: add anything else.
- **Larger test sizes (100K, 1M rows):** TODO: explain how these were made.
- **Limitations and license:** TODO: copy the license from the Kaggle page.
- The CSV is not committed. Download it from Kaggle and save it as `data/NVDA.csv`.

## 4. Algorithms implemented
All three are written by us, with no library shortcuts. Each returns `(buy_index, sell_index, profit)`.

1. **Brute force (baseline):** checks every buy day and every later sell day.
2. **Divide and conquer (efficient):** splits the daily changes in half; the best window is in the left half, the right half, or crosses the middle.
3. **Kadane's algorithm (optimized):** one pass through the data, tracking the best running window.

## 5. Complexity summary
| Algorithm | Time | Extra space |
|---|---|---|
| Brute force | O(n²) | O(1) |
| Divide and conquer | O(n log n) | O(log n) |
| Kadane | O(n) | O(1) |

## 6. Major experimental results
TODO: paste the table from `results/benchmark_results.csv` and summarize whether measurements matched the theory.

| Input size | Brute force | Divide and conquer | Kadane |
|---|---|---|---|
| 1,000 | | | |
| 10,000 | | | |
| 100,000 | | | |
| 1,000,000 | | | |

## 7. Technologies used
Python 3, pandas, matplotlib, pytest, yfinance (optional), GitHub, GitHub Pages.

## 8. How to run the project
```bash
# Find the best buy/sell window with all three algorithms
python -m src.cli --csv data/NVDA.csv --start 2015-01-01 --end 2020-12-31

# Run the benchmarks (writes to results/ and figures/)
python benchmarks/run_benchmarks.py --csv data/NVDA.csv
```

## 9. Testing instructions
```bash
python -m pytest tests/
```
The tests check known examples, no-profit cases, and that all three algorithms agree on random data.

## 10. Project structure
```
src/algorithms/   brute_force.py, divide_conquer.py, kadane.py
src/              data_loader.py, cli.py
tests/            test_algorithms.py
benchmarks/       run_benchmarks.py
results/          benchmark output tables
figures/          charts
docs/             technical paper and outlines
presentation/     slides
index.html        GitHub Pages website
```

## 11. Contributors and their roles
See [CONTRIBUTIONS.md](CONTRIBUTIONS.md) for the full breakdown.

| Member | Role |
|---|---|
| Name 1 | Data loading and cleaning |
| Name 2 | Brute force algorithm and tests |
| Name 3 | Divide-and-conquer algorithm and tests |
| Name 4 | Kadane algorithm and tests |
| Name 5 | Benchmarks, charts, and website |

## 12. GitHub Pages website
TODO: add the link once Pages is published.

## 13. Technical paper
TODO: link to the paper in `docs/`

## 14. Presentation
(https://docs.google.com/presentation/d/1rM4b4HYKq6ne0tCXuWrXCAXHIAWELuxF/edit?slide=id.p1#slide=id.p1)
