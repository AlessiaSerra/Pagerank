# PageRank Power Method Implementation

This repository contains a MATLAB implementation of the PageRank algorithm using the Power Method. It includes a script that processes web graph data and calculates page importance, alongside a real-world dataset representing the web graph of Hollins University.

## Files Included

*   `pagerank.m`: The main MATLAB script that executes the PageRank algorithm.
*   `hollins.dat`: A text-based dataset containing 6,012 nodes and 23,875 edges, where the first line specifies the dimensions, the following lines map node indices to URLs, and the final section contains the edge list (source to destination).

## Features

*   **Interactive Dataset Selection**: The script prompts the user to select between the `hollins.dat` dataset, a predefined 4x4 test matrix, or a predefined 5x5 test matrix.
*   **Sparse Matrix Processing**: Reads the dataset by skipping the first $N+1$ header lines to extract source and destination nodes, building a sparse adjacency matrix to optimize memory.
*   **Stochastic Matrix Construction**: Converts the adjacency matrix into a column-stochastic matrix while identifying and tracking "dangling nodes" (nodes with an out-degree of zero).
*   **Power Method Execution**: Iteratively computes the PageRank vector by factoring in direct link contributions, dangling node contributions, and random teleportation.
*   **Top-K Ranking Output**: Sorts the final PageRank vector in descending order and prints the top 10 nodes for the `hollins.dat` dataset or all nodes for the smaller test matrices.
*   **Verification**: Includes a `checkPageRank` function to verify that the final vector sums to 1 and calculates the Rayleigh quotient.

## Algorithm Parameters

The algorithm uses the following predefined parameters to control the Power Method calculations:
*   **Teleportation factor ($m$)**: $0.15$
*   **Damping factor ($d$)**: $0.85$ (calculated as $1 - m$)
*   **Convergence tolerance (`tol`)**: $1e-6$
*   **Maximum iterations (`max_iter`)**: $1000$
*   **Initial vector ($x$)**: A uniform distribution vector initialized as $1/N$ for all nodes

## Usage Instructions

1. Ensure both `pagerank.m` and `hollins.dat` are located in the same working directory.
2. Run the `pagerank_finale.m` script in MATLAB.
3. When prompted in the console, input `1` to run the algorithm on the Hollins University dataset, `2` for the 4x4 matrix, or `3` for the 5x5 matrix.
4. The console will display the top ranked nodes with their specific PageRank scores, followed by a message indicating how many iterations were required to achieve convergence.
