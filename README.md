# CS 680 Advanced Algorithms

Graduate coursework by **Malgorzata Debska** for **CS 680 Advanced Algorithms** at Southern New Hampshire University.

This repository documents my work designing, implementing, and evaluating algorithms. Throughout the course, I used Python to solve problems involving sorting, searching, trees, recursion, and compression. I used Big-O analysis to explain how algorithms scale and measured runtime and memory use to understand how they perform on actual data.

## Projects and Activities

| Project or activity | What I worked on |
| --- | --- |
| **Project One — Data analysis and algorithm design** | Reviewed four datasets and evaluated algorithms for validating records, calculating statistics, counting words, and searching data. Proposed data structures suited to each task. |
| **Project Two — Huffman compression** | Built a standalone Python application that compresses CSV files and restores them without losing data. Created a test plan and measured correctness, storage savings, and performance. |
| **Sorting and searching** | Compared insertion sort, merge sort, and quicksort. Practiced sorting records and finding entries in a dataset. |
| **AVL tree search** | Implemented a self-balancing binary search tree for word lookup and tracked how many nodes each search visited. |
| **Recursion and functional programming** | Practiced recursive problem solving, functional constructs, and exception handling. |
| **DNA sequence matching** | Defined expected outputs and success criteria for an exact sequence-matching exercise. |
| **Algorithm testing** | Designed test cases for successful searches, missing values, and edge cases. Used execution results to evaluate correctness and performance. |

## Guide to the Files

| File or file type | What it contains |
| --- | --- |
| **Python files (`.py`)** | Source code for course activities and projects, including implementations for searching, sorting, and compression. |
| **CSV datasets (`.csv`)** | Input records used to run and test the programs. Use the dataset associated with the activity you want to run. |
| **Project One report** | Dataset requirements, algorithm comparisons, and recommendations for validating, analyzing, and retrieving records. |
| **`huffman.py`** | The Project Two application. It supports compression, decompression, and round-trip verification. |
| **`CS680_Huffman_Test_Plan.docx`** | The testing procedure, performance metrics, edge cases, and pass criteria for the Huffman application. |
| **`CS680_Huffman_Technical_Report.docx`** | The application design, Big-O analysis, benchmark results, execution screenshots, and possible improvements. |

## Featured Project — Lossless Huffman Compression

The Huffman application counts byte frequencies and uses a min-heap to build a Huffman tree. It gives frequent bytes shorter codes, writes a compressed archive, and uses the stored frequency information to rebuild the tree during decompression. The program checks the restored data with SHA-256 and compares the restored file to the original byte for byte in verification mode.

I tested all four datasets in the VS Code terminal on my iMac. Every restored file matched its original exactly.

| Dataset | Original bytes | Archive bytes | Size reduction | Round trip |
| --- | ---: | ---: | ---: | --- |
| 1 | 138,346 | 88,067 | 36.34% | Pass |
| 2 | 14,102,720 | 8,762,180 | 37.87% | Pass |
| 3 | 14,099,977 | 8,759,876 | 37.87% | Pass |
| 4 | 14,104,578 | 8,763,039 | 37.87% | Pass |

Decoding was the slowest stage because the implementation walks the Huffman tree one bit at a time. The technical report discusses how a decoding lookup table could speed up that step and how buffered file processing could reduce memory use for larger inputs.

### Run the Huffman Project

Use Python 3 and open a terminal in the folder containing `huffman.py` and your input CSV. Replace `sample.csv` with your actual filename and use a new output folder for each run.

```bash
python3 huffman.py verify "sample.csv" verification_output
```

The command creates `compressed.huf` and `restored.csv` inside `verification_output`. It displays read and write timings, encoding and decoding times, storage savings, and `Byte comparison: PASS` when the restored file exactly matches the original.
