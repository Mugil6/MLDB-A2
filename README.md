# Min-Hashing and Locality Sensitive Hashing (LSH)

This repository contains the implementation of Min-Hashing and Locality Sensitive Hashing (LSH) algorithms designed to efficiently identify similar items within large datasets. It was developed as part of Assignment 2 for CSL7110.

## 📌 Project Overview
Finding similar items using a brute-force $O(N^2)$ comparison is computationally unfeasible for massive datasets. This project solves this by:
1. **Min-Hashing:** Compressing large sets (k-grams of text or user-item interactions) into smaller, fixed-size signatures while preserving the approximate Jaccard similarity.
2. **Locality Sensitive Hashing (LSH):** Utilizing a band/row architecture to hash these signatures into buckets, ensuring that highly similar candidate pairs hash to the same bucket without needing to evaluate every possible pair.

## 🗂️ Repository Structure
* `main.ipynb`: The core Jupyter Notebook containing all algorithmic implementations, optimized execution scripts, and inline outputs.
* `minhash/`: Directory containing the initial text documents (`D1.txt` to `D4.txt`) used for k-gram analysis.

## 🚀 Key Features & Optimizations
* **Custom K-Gram Generation:** Supports both character-level and word-level k-gram sets.
* **Universal Hash Families:** Implements a robust `MinHash` class utilizing $h(x) = (ax + b) \pmod m$ mapping with `zlib.crc32` for deterministic string-to-integer conversion.
* **Optimized Set Operations:** Replaces standard Python loops with native C-backed set operations (bitwise intersections) to drastically reduce the execution time over $444,153$ user pairs.
* **Probability S-Curves:** Implements the $1 - (1 - s^b)^r$ probability bound to mathematically tune the LSH threshold.

## 🛠️ Execution Requirements
To run this notebook locally, you need Python 3.x and the standard built-in libraries. No external machine learning libraries (like Scikit-Learn or Pandas) are required, as the algorithms are built from scratch.

```bash
# Clone the repository
git clone https://github.com/Mugil6/MLDB-A2
cd MLDB-A2

# Launch Jupyter Notebook
jupyter notebook main.ipynb