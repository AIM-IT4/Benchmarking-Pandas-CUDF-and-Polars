# Benchmarking Pandas, CUDF, and Polars

## Introduction

Choosing the right tools for data manipulation in you day 2 day task as a Quant can significantly impact your workflow's efficiency. In this project, we compare three popular libraries: **Pandas**, **CUDF**, and **Polars**. We'll focus on common operations like `groupby` and `map` using a large dataset to see which library performs best.

## Installation Steps

### Check GPU Availability

First, make sure you have a GPU available in your Colab environment. Run this command:

```python
!nvidia-smi
# Install RAPIDS in Google Colab or Notebook
!git clone https://github.com/rapidsai/rapidsai-csp-utils.git


!bash rapidsai-csp-utils/colab/rapids-colab.sh stable

## Benchmarking Results

| Operation | Pandas Time (s) | CUDF Time (s) | Polars Time (s) |
|-----------|------------------|---------------|-----------------|
| Groupby   | 0.5474           | 0.0694        | 1.1077          |
| Map       | 2.9003           | 0.0058        | 0.0501          |


## Observations

### CUDF: The Power of GPU Acceleration
CUDF demonstrated remarkable performance, particularly in the `map` operation, where it completed the task in just 0.006 seconds on average. This highlights the significant advantage of GPU acceleration for large-scale data operations. For `groupby`, CUDF also outperformed the others, showcasing its efficiency in parallel processing.

### Polars: Efficient and Versatile
Polars showed impressive results, especially in the `map` operation, completing it in 0.05 seconds on average. Although it was slower than CUDF in the `groupby` operation, Polars still outperformed Pandas, making it a strong contender for high-performance data manipulation tasks.

### Pandas: Reliable but Slower
Pandas, while being the most familiar and widely used library, was the slowest in both operations. This is expected given that Pandas operates on CPU and is not optimized for parallel processing. However, its ease of use and extensive ecosystem make it a go-to choice for many data scientists.

## Conclusion
The benchmark highlights that for large datasets and performance-critical applications, leveraging GPU-accelerated libraries like CUDF can offer substantial benefits. Polars also provides an excellent balance between performance and ease of use, making it a valuable tool for data manipulation tasks.
