# `awk`
- Its a powerfull text processing tool used for pattern scanning, extracting and manipulating data.
- It works by splitting text into fields based on seperators (default ' ', and we can give custom seperator using `-F` flag.), and accessing those fields based on sequence: $1, $2,..etc.

## Basic Syntax: ``awk 'pattern { action }' FILE``

## Example usage:

```sh
# Print the first column of a file
awk '{print $1}' file.txt

# Print lines where the second column is greater than 50
awk '$2 > 50' file.txt

# Print the sum of values in the second column
awk '{sum += $2} END {print sum}' file.txt

# Use a custom field separator (CSV file processing)
awk -F"," '{print $1, $3}' data.csv

# Print lines containing 'error' in a log file
awk '/error/ {print}' log.txt
```

