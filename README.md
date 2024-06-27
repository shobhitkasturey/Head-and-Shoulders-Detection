

### README File: `README.md`

```markdown
# Head and Shoulders Pattern Detection

This repository contains a Python script that detects the "Head and Shoulders" pattern in stock market data from a CSV file and outputs the detected patterns to a new CSV file.

## Requirements

- Python 3.x
- pandas

## Installation

1. Clone the repository or download the script.
2. Install the required Python package using pip:
    ```bash
    pip install pandas
    ```

## Usage

1. Ensure your candlestick data is in a CSV file named `candlesticks.csv` in the same directory as the script. The CSV file should contain the following columns:
    - `Open`
    - `Close`
    - `High`
    - `Low`

2. Run the script:

    ```bash
    python detect_head_and_shoulders.py
    ```

3. The script will create a new CSV file named `head_and_shoulders.csv` containing the rows where a Head and Shoulders pattern was detected.

## How it Works

The script performs the following steps:

1. Reads the input CSV file `candlesticks.csv` into a pandas DataFrame.
2. Defines a function `is_head_and_shoulders` that checks if a given row of candlestick data represents a Head and Shoulders pattern. The function ensures:
    - The head (current row's high) is higher than both the left shoulder (two rows before) and the right shoulder (two rows after).
    - The left and right shoulders are at similar levels (within 10% of the head height).
3. Iterates over the DataFrame and applies the `is_head_and_shoulders` function to detect the pattern.
    - The loop `for i in range(2, len(df) - 2):` iterates from the 3rd row to the 3rd last row of the DataFrame. This is because the detection function checks two rows before and two rows after the current row. Starting at index 2 ensures there are always enough preceding rows to check for the left shoulder, and stopping at `len(df) - 2` ensures there are always enough following rows to check for the right shoulder.
4. Creates a new column `HeadAndShoulders` in the DataFrame that is `True` if the row represents a Head and Shoulders pattern.
5. Filters the DataFrame to include only the rows where the `HeadAndShoulders` column is `True`.
6. Writes the filtered DataFrame to a new CSV file `head_and_shoulders.csv`.

## Example

Input CSV (`candlesticks.csv`):
```
Open,Close,High,Low
10,15,20,5
12,18,19,10
13,11,16,10
15,20,22,14
...
```

Output CSV (`head_and_shoulders.csv`):
```
Open,Close,High,Low,HeadAndShoulders
15,20,22,14,True
...
```

## Contact

For any questions or suggestions, please contact:

Shobhit Kasturey  
Email: shobhitkasturey@gmail.com


```

